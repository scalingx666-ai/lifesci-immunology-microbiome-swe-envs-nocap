# Issue

**Title:** [MRG] allow multiple targets with conf/run

## Description

e.g. `conf/run dory-test extract_contigs extract_reads` will build, search, extract contigs, and extract reads. Previously this would have had to be two commands, `conf/run dory-test extract_contigs; conf/run dory-test extract_reads`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `331f6ed3f9c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.