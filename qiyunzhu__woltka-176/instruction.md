# Issue

**Title:** Improve command-line interface

## Description

Modified CLI. Now the `tools` menu is gone. All commands are raised to the main interface. For example, `woltka tools collapse` becomes `woltka collapse`. Also let any command show help information if no parameter is given.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ea6295b3f1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.