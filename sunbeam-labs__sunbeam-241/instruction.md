# Issue

**Title:** Sunbeam version 2.1.0

## Description

* [X] I have run `bash tests/test.sh` on a local deployment and the tests passed successfully
* [X] If this adds a new output file, I have added a check to tests/targets.txt
* [X] If this fixes a bug, I have added an appropriate test to tests/test.sh

This pull request from `release-2.1.0` to `stable` incorporates a number of fixes for recent issues:

 -   Updates to documentation (#169, #230, #231)
 -   Fix missing samtools (#224)
 -   Integration test updates to schedule weekly builds (#222)
 -   Fix issues with old paired-end illumina adapters (#221)
 -   Script updates to use conda commands instead of source commands (#220)
 -   Add h5py package explicitly to avoid dependency metadata problem (#219)
 -   Add multiQC to build QC report (#203)
 -   Use multithreading for cutadapt in QC (#202)
 -   Correct conda channel priority during install (#201)
 -   Update documentation to spell out requirements (#199)
 -   New megahit failure handling (#194)
 -   Enforce sample wildcard constraints in Snakemake rules (#190)
 -   Run megahit multithreaded (#189)

I also added a build manifest, which is run every time on integration testing!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `287670ef27bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.