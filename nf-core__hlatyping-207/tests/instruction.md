# Issue

**Title:** Fix conda tests by updating Nextflow to 25.04.2

## Description

## Summary

- Update Nextflow version from 25.04.0 to 25.04.2 in CI workflow

Nextflow 25.04.0 uses the deprecated `--mkdir` flag when creating conda environments, which was removed in conda 25.1+. This causes conda tests to fail with:

```
conda: error: unrecognized arguments: --mkdir
```

Nextflow 25.04.2 includes the fix () that removes the obsolete `conda create --mkdir` option.

Fixes the conda test failures in #206.

## Test plan

- [ ] Verify conda tests pass in CI

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16aec13ff3bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.