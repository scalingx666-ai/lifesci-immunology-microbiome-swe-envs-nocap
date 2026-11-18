# Issue

**Title:** `sunbeam init` and `sunbeam config update` now add extension config options

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [X] If this fixes a bug, I have added an appropriate test to tests/test.sh

This PR adds functionality to `sunbeam init` and `sunbeam config update`. Both of these now look within each extension in the extensions folder for a file named `config.yml`. If this file is found, those config options are now added to config files made by `sunbeam init` and `sunbeam config update`. Tests for both of these functions are included. This .

I also cleaned up sunbeamlib a bit. The `config.py` file within the `scripts` subdir was unused (and older than the `_config.py`, which is used).

Finally, I discovered a weird feature/bug in CircleCI, where if you have a file named "config.yml" in your repo, for some reason it gets dropped when CircleCI clones it in. Mostly leaving this description here in case anyone else has this problem in the future.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8927cf106b45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.