# Issue

**Title:** Linting fixes

## Description

To get markdown/yml lint working, even if nf-core lint will continue to fail

- Adds GHA fixes that were added by nf-core/core to template before the switch to prettier
- Adds a YAML lint config file, to allow 'template' files to pass (otherwise nf-core linting would fail)
- Fixes all the markdown linting errors accordingly

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `feaa7a621da3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.