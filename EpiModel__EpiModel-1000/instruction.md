# Issue

**Title:** Update pkgdown.yaml

## Description

## Summary

- Remove `pull_request` trigger from the pkgdown workflow so it only runs on pushes to main/master, releases, and manual dispatch
- Simplify concurrency group and remove the now-unnecessary PR guard on the deploy step

The pkgdown build was running on every PR commit (~5-10 min of runner time) but never deploying the result. R CMD check already catches the Roxygen issues most likely to break pkgdown, so the PR build provided little value relative to its cost.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47b6c8663711`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.