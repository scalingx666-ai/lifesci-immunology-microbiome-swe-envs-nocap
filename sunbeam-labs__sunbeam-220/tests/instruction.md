# Issue

**Title:** Use "conda activate" instead of "source activate"

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully

This PR is related to issue #198 (and was also brought up in #204 by @scottdaniel). Now the install and test scripts use "conda [de]activate" rather than "source [de]activate". No more warnings!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f46ae8cafbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.