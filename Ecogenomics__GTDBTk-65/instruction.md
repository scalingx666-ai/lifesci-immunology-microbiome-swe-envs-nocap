# Issue

**Title:** Implements full custom MSA filtering and tree inference.

## Description

I have moved the trim_msa.py script into the GTDB-Tk source code directory. GTDB-Tk align now supports the same custom trimming we plan to perform. The trim_msa.py script can still be run independently of GTDB-Tk if required. I also finalized the implementation for inferring trees with FastTree.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2e03a0f29ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.