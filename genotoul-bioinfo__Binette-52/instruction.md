# Issue

**Title:** Improve pyfastx index management

## Description

This PR attempts to fix the error related to pyfastx, as reported in issue #49.

To resolve the issue, the approach has been modified:
- pyfastx.Fasta which produce the fasta file index, is now used only when writing the final bin.
- pyfastx.Fastx is used for protein prediction and initial contig parsing to avoid multiple accesses to the index file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e68fc0d5c77a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.