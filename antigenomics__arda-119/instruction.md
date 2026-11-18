# Issue

**Title:** 2.26.0

## Description

## Added

**`arda scenarios`** — a generative recombination model estimated from nucleotide junctions by EM over scenarios, written in the same long `locus/kind/key/value` table `d_prior.tsv` uses, so `arda.dpost` can stop marginalising OLGA's numbers. A scenario is not identifiable from sequence (4,346 tuples reproduce one real human TRB junction exactly), so the tallies are expected counts summed over scenarios, never one MAP reading. An insertion costs its own sequence (`0.25^len`), not just its length — without that, EM explains the whole junction as insertion.

**`arda.hmm`** — the same recursion read as inference: `log_likelihood` (the marginal), `posterior_d`, `best_scenario`. Does not replace `arda.dpost` and gates nothing.

**AIRR `umi_count`** (`correct --cell-from`) — distinct UMIs, not distinct records. Omitted, never 0 or 1, when the dialect names no UMI.

**`docs/productivity.rst`** — what `productive` / `stop_codon` / `vj_in_frame` actually mean, taught with real GenBank reads rather than prose.

## Faster

The scenario estimator is **4.7× quicker** (17.74 s → 3.79 s per EM iteration on 2,496 real records) with byte-identical output — and entirely in Python. Profiled first: the cost was 73.5 M dict updates from distributing flank weight per term instead of per span, not the germline matching.

## Fixed

A wrong premise about `dnaio` recorded in four places (it does not drop the FASTQ comment — arda does, by taking `.id`). Two stale open loops closed: `v_identity` is neither gated nor deleted, and `_SEGMENT_FORMAT` already carries `tend`.

## Release checklist

- [x] `pyproject.toml` and `src/arda/__init__.py`
- [x] `CHANGELOG.md` section
- [x] Nextflow module bumped in all four places — `environment.yml`, `main.nf` container tag, `Dockerfile`, `README.md` (item 5, which no CI job covers)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfdb70649675`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.