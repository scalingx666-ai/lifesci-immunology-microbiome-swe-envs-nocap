# Issue

**Title:** Add help parameter to concatenate.py script

## Description

Hi,

I was taking some time to understand how to check the help for the `concatenate.py` script. I hope this change will make accessing the help prompt easier.

Summary of changes:
  - Add `-h/--help` flags to concatenate.py

  Previously, only running `concatenate.py` with no arguments printed the
  help command. Now, the user can call the script w/ the `-h/--help` flags.
  Additional flags can be added to L22.

Best,
V

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8dc1a7146dbd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.