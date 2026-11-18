# Issue

**Title:** Add help text for --coverage-samples-per-job

## Description

`--coverage-samples-per-job` had `help=''`. argparse skips empty help entirely, so `--help` showed neither a description nor the default.
  This adds a description; the default now displays too.

  Help display only, with no change to behaviour. The test suite was not run.

  🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42a014ff9235`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.