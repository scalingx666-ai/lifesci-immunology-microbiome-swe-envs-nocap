# Issue

**Title:** Update docs

## Description

* [x] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [x] If this adds a new output file, I have added a check to tests/targets.txt
* [x] If this fixes a bug, I have added an appropriate test to tests/test.sh
* [x] If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f90debd0bc5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.