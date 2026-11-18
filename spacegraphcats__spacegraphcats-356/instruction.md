# Issue

**Title:** require that some reads be paired, by default

## Description

Turn read pairing requirements on by default, which was my original intent for #344 but got lost in testing/tweaking.

Also fixed a typo ;).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32fc63825197`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.