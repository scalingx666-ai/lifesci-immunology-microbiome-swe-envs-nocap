# Issue

**Title:** Simplify install process for sunbeam extensions

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [X] If this fixes a bug, I have added an appropriate test to tests/test.sh

This PR introduces a new subcommand: `sunbeam extend`, which installs Sunbeam extensions from a GitHub repository URL. The `sunbeam extend` logic is encapsulated in the new file `sunbeamlib/scripts/extend.py `. Other inclusions: new test, README update, documentation updates describing this new feature. This PR .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e657bcb7e302`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.