# Issue

**Title:** Split get coverage into separate jobs when many samples

## Description

- [x] Move hardcoded paths to variables
- [x] Add split/gather coverage rule alternative (split into groups of n samples with long-reads last)
- [x] Add `--coverage-job-strategy` arg with `default` (when >=10 samples), `never`, `always` as options
- [x] Add `--coverage-samples-per-job` arg with default of 5
- [x] Test short-read
- [x] Test short+long
- [x] Test long-read
- [x] Test real world

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `177fcd095965`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.