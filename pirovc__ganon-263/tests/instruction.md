# Issue

**Title:** Feature/multiple matches classify

## Description

- new arg: `ganon classify -m/--multiple-matches em/lca/skip`
  - `em` executes `ganon reassign` after `ganon classify`
- new args: `ganon classify --min-count --report-type --skip-report` to better control reports from classify
- output file `.lca` is now `.one` in `ganon-classify`, `ganon classify` and `ganon report`
- updated docs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f44cc34d4a9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.