# Issue

**Title:** Merge paired end reads

## Description

As dicussed in #20 , I think it is possible to have single-end and interleaved paired end files in one file. I have here a first version of a rule which merges the paired end files. 

I don't know ho to check the condition if the reads are paired or not. 

using the, `fastq_file`  variable we can guide the input/output files easily trough the different conditions.
I removed one decontamination rule, which seems to be a duplicate.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `681d733c3ba0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.