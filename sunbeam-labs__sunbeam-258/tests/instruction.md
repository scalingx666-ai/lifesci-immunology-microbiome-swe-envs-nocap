# Issue

**Title:** Easier installation for extensions

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully

This PR (re)introduces a new subcommand: `sunbeam extend`, which installs Sunbeam extensions from a GitHub repository URL. The `sunbeam extend` logic is encapsulated in the new file `sunbeamlib/scripts/extend.py `. Other inclusions: new test, README update, documentation updates describing this new feature. Related to #251.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bfece2a90ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.