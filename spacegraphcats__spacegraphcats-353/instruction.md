# Issue

**Title:** Make default spacegraphcats interface use the `click` API

## Description

Swap `click.py` into `__main__`. Also fix `init` command. Cleans up snakefile a bit too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05bc82c2b330`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.