# Issue

**Title:** 2.25.0 — the unmapped ledger and the FR4 stop scan

## Description

Two changes already on `master` plus the version bump.

## Why a read did not map ()

`mapped_fraction` alone made "wrong organism", "no receptor content" and "`--min-score` too
strict" into one number. `run/map` now carries an `unmapped.*` ledger — `prefilter_rejected`,
`no_hit`, `hit_not_in_reference`, `constant_only`, `below_min_score` — with each also in the
`sample` scope as a fraction of `total_reads`.

It **adds up**: on `tests/data/rnaseq_real`, 453 + 788 + 8 + 54 + 17 = 1,320, and a four-read-group
run reports an identical ledger. `accounted` is recomputed on a shard merge rather than summed, so
a bucket missing from the merge shows as a shortfall instead of looking balanced.

## A stop codon in FR4 ()

The junction ends **at** [FW]118, FR4's first residue, so FR4 residues 2..n were scanned by
neither `productive` nor `stop_codon`. Now scanned. Measured first: none of 4,217 evaluable
fixture rows carries an FR4 stop, so the fix left all 4,843 annotated rows byte-identical.

## Also

`seqtree` floored at `>=1.0,<2`, verified against the full suite.

## Verification

- `ruff check src/` clean, `make -C docs html` (`-W`) zero warnings
- **1,088 passed**, 9 skipped
- Nextflow module bumped in `environment.yml`, `main.nf`, `Dockerfile` and its `README.md`

## Not in this release

The `vj_in_frame` question is recorded in `ROADMAP.md` with the read-by-read evidence and left
for your decision — see the closing note on the PR thread.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd3e30d9b568`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.