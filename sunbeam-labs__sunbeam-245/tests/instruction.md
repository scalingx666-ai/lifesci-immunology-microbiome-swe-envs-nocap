# Issue

**Title:** Conda env for adapters

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [X] If this fixes a bug, I have added an appropriate test to tests/test.sh

, . This PR removes all references to the `conda_fp` in `sunbeamlib`, and replaces the `adapter_fp` config key with `adapter_template` to reflect the fact that the adapters are now dynamically resolved on runtime (and not hardcoded filepaths). The trimmomatic rules have also been updated to reflect this new config key.

I also added a test to make sure config updating works as expected!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cac2572a28a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.