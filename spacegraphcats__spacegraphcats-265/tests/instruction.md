# Issue

**Title:** [WIP] add better error message & early exit for empty catlas

## Description

If (for whatever reason) the catlas is empty, exit and provide an error message.

Comes with test files!

Addresses #259.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3362367dfb8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.