# Issue

**Title:** create neccessary "mountpoints"

## Description

Assume a user wants to set-up a fresh Qiita instance. She/he probably changes the `BASE_DATA_DIR` and eventually executes `qiita-env make`.

This process will most likely fail, as the expected sub-directories of the `qiita.data_directory` relation not yet exist. Therefore, this PR adds a function `create_mountpoints`, which is called within the `patch` mechanism.

If instance is in test mode, the sub-directories not only need to exist, but also be populated with the test data, which are located in `support_files/test_data/`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdad618cc628`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.