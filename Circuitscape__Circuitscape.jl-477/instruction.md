# Issue

**Title:** CI: test on the minimum supported Julia as well as latest

## Description

`Project.toml` declares `julia = "1.11"` but the matrix only ran `'1'` (currently 1.12), so the lower bound was never exercised. Adds one `'min'` configuration on `ubuntu-latest`; `min` resolves to whatever the compat lower bound is, so it stays correct when compat is bumped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6c8623eff5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.