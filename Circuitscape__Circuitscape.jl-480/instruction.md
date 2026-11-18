# Issue

**Title:** Stop exporting `start`

## Description

`start` is a generic name to put in every user's namespace for an interactive INI builder. The README already shows the qualified form, and `Circuitscape.start()` continues to work (INIBuilder is `using`-ed into the module). The docs sentence that referred to a bare `start()` is updated to match.

Full suite passes locally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3a1f97cde4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.