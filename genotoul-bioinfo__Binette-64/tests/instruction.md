# Issue

**Title:** fix bad implementation when checking duplicated contigs in input sets

## Description

A simple check on whether contigs are duplicated in an input bin set was badly implemented making this check quite long when the number of contig is important. 

This PR fix it by using Counter. 

Fix partially issue #62

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `947d05d35faa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.