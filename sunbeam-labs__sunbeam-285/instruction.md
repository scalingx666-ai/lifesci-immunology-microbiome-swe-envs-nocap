# Issue

**Title:** added sanity check to warn against installing from a .tar.gz git archive, which raises a setuptools_scm error

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [ ] If this adds a new output file, I have added a check to tests/targets.txt
* [ ] If this fixes a bug, I have added an appropriate test to tests/test.sh
* [ ] If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`

This attempts to address a confusing situation (at least for me) when trying to install Sunbeam from a git archive instead of a clone of the repo

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0e29cd47490`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.