# Issue

**Title:** Warn when using CHOLMOD solver with large grids

## Description

## Summary
- Warns users when CHOLMOD is selected and the landscape exceeds 5M cells, recommending `cg+amg` instead

## Test plan
- [ ] Verify warning appears with CHOLMOD solver on a grid > 5M cells
- [ ] Verify no warning with `cg+amg` solver
- [ ] Verify no warning with CHOLMOD on a grid < 5M cells

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e75982590399`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.