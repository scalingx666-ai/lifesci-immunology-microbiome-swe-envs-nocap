# Issue

**Title:** Show final details (Vaccine type, auto book, etc) before staring search.

## Description

This shows all final selected information.

- Vaccine type
- Auto book status (`True` or `False`)
- Start date for slot search
- Refresh interval in seconds
- Minimum slots to search for

Re-submitting as requested, in `ext-dev/info-screen`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56df36e8ad54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.