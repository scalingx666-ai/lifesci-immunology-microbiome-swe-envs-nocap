# Issue

**Title:** Add multiQC to build QC report

## Description

## Description

As promised, here is another PR, more as a POC for the use of [MultiQC](https://multiqc.info/) in the `qc` step.

In the future, if the rule is also used in other steps to get a summary of them, I guess we could put it in an independant `.rules` file and include this generalized rules in every concerned step.

Since a new rule is here added and I was not sure on the way to proceed, I apologize in advance if I put things in the incorrect place or named variable without respecting your own development rules.

## Validations

* [x] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [x] If this adds a new output file, I have added a check to tests/targets.txt
* [x] ~If this fixes a bug, I have added an appropriate test to tests/test.sh~
* [x] ~If this adds or modifies a rule that uses FASTQ files, the input accepts gzipped FASTQ and outputs gzipped FASTQ, or marks uncompressed FASTQ output as `temp`~

Cheers,
Kenzo

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f592b6cc2e8c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.