# Issue

**Title:** Add support for sequence IDs with read suffix (Old Illumina)

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [X] If this fixes a bug, I have added an appropriate test to tests/test.sh
* [X] If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`

This changes the graph at the very start of the QC rules to optionally strip off a configurable suffix for sequence IDs, to ensure that pairs always use the same ID, as generally expected.  .  (If this feature isn't enabled it will just symlink the original files into place instead.)  This allows us to work with older-style Illumina sequence IDs that end with /1 and /2 for R1 and R2, or any other suffix pattern that might be used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8091d8e9dee0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.