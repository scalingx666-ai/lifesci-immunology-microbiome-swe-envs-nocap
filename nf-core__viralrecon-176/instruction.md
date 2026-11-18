# Issue

**Title:** Parse fastp log instead of NF countFastq() to filter empty FastQ files after trimming

## Description

This is a much more efficient way of doing the same thing because we no longer have to parse the entire FastQ file to determine the total number of reads remaining after trimming. We are just parsing the JSON file dumped by fastp instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76069cc6de6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.