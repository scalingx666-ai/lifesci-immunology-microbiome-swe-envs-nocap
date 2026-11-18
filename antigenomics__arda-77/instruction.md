# Issue

**Title:** Rebuild a stale mmseqs cache instead of trusting its presence

## Description

## Problem

Two mouse GenBank tests fail (`tests/unit/test_genbank_receptors.py::test_mouse_records_map_and_are_productive`, `test_mouse_fr4_agrees_between_vj_and_jc_scaffolds`): the mouse junction comes out one codon early, e.g. `junction_aa='LCASSFHRDYNSPL'` instead of the canonical `CASSFHRDYNSPLYF`.

## Root cause — a stale target-DB cache that never rebuilds

Not a transfer or reference-build bug. The committed `alleles.fasta` / `markup.tsv` are correct. The local `data/mmseqs_db/<org>_<seqtype>` cache held a **352-nt** `TRB_284` from an older reference, while the reference had since been rebuilt to **346 nt**. The runtime projected the 346-nt markup coords through an alignment against the stale 352-nt scaffold → 6 nt of drift → junction slides off Cys104.

`_cached_target_db` *does* detect the staleness (cache db mtime `<` `alleles.fasta` mtime) and calls `_createdb_atomic` to rebuild. But `_createdb_atomic` gated its "already built" check on `done=db.exists` (from the concurrency-safety refactor in `0fe3209`). The stale db file exists, so the guard called the work done and returned **without rebuilding**. The stale cache was effectively permanent.

This bites any user whose reference changes under an existing cache — a `build-db`, or a pulled `alleles.fasta`. `build-index` had the same latent skip after a `build-db`.

## Fix

"Done" now means a **current** db, not merely a present one: `db.exists() and db.stat().st_mtime >= target_fasta.stat().st_mtime`. A cache older than its source fasta is rebuilt; the concurrency guarantees (atomic temp-dir build, `db` moved into place last) are unchanged.

## Tests

- `tests/unit/test_index_concurrency.py::test_a_stale_cache_is_rebuilt` — new regression guard (fails without the fix: stale db exists → old guard skips → stays stale).
- Full CI set (`tests/unit tests/synthetic tests/realworld`) green: 302 passed; both mouse tests now pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a203a2999dcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.