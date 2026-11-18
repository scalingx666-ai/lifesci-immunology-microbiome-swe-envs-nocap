# Issue

**Title:** Update multiqc wrapper to newest version.

## Description

There is an error in the rule `multiqc_mapping_genome` due to an incomptability with python 3.12 (see ). The problem comes from an incompatibility of MultiQC with Python3.12, which was fixed . 
Atlas uses a very old wrapper for multiqc and updating it should fix the issue.

This should fix

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae7816112115`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.