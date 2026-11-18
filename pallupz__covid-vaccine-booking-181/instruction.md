# Issue

**Title:** Press enter to refresh immediately during countdown for next refresh.

## Description

During the message "No viable options..." press Enter to immediately refresh.
Example:
```
Centers available in 560049 from 22-05-2021 as of 2021-05-21 18:16:29: 0
No viable options. Press enter to refresh immediately. Next update in 8 seconds...
===================================================================================
Centers available in 560066 from 22-05-2021 as of 2021-05-21 18:16:35: 0
Centers available in 560067 from 22-05-2021 as of 2021-05-21 18:16:35: 0
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb0f8b25bd05`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.