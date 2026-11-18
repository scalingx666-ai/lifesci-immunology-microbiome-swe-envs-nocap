# Issue

**Title:** Re-add CompatHelper workflow

## Description

Only `ci.yml` and `TagBot.yml` remain under `.github/workflows`; the old `compathelper/*` branches show it used to run. Dependabot is configured for GitHub Actions only, so Julia compat bumps have had to be noticed by hand (e.g. AlgebraicMultigrid 1 → 2 in #471).

Uses `DOCUMENTER_KEY` as the SSH key so the PRs it opens trigger CI, same as TagBot does.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c782de05c1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.