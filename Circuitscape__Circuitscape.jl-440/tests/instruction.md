# Issue

**Title:** Fix INIBuilder ground file menu in advanced mode

## Description

## Summary
- Fixed bug where the ground file selection menu in advanced mode assigned the options list directly to `n` instead of presenting a `RadioMenu`
- This made it impossible to select a ground file path in the INIBuilder's advanced mode flow

## Test plan
- [ ] Run `Circuitscape.INIBuilder.start()`, choose advanced mode, and verify ground file step presents a working menu

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e75982590399`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.