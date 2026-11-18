# Issue

**Title:** added sep argument in read_biom2phyloseq.R

## Description

This only applies for meta-data as separator is irrelevant for BIOM files. Default sep for read.csv is (of course) ",".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62f05120b05f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.