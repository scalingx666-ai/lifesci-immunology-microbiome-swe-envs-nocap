# Issue

**Title:** Address issue #182

## Description

update "intro_radEmu" vignette to use `test_kj` argument whenever we run score tests (previously the unevaluated example that runs all score tests for the group covariate in line 245 was outdated and missing `test_kj`), note in `phyloseq` and `tse` vignettes that an example of running hypothesis tests is in the "intro_radEmu" vignette.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53db71887be9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.