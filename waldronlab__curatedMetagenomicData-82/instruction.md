# Issue

**Title:** Add WDL and Dockerfile

## Description

The WDL in this pull request contains a workflow to run metaphlan
from an array of SRA accessions. The first step runs fastq-dump
on the accessions and the second runs a basic metaphlan workflow 
based on the metaphlan workflow from @stevetsa.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3553bcca76e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.