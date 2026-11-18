# Issue

**Title:** add dockerfile to install options

## Description

Thank you for providing this useful package.

I've created a simple Docker image of this tool for use in cloud orchestration eg. with Nextflow and thought I'll contribute the Dockerfile back to this repo (image built using python 3.6 and biom-format 2.1.10). This will allow anybody to build a docker image locally and run it interactively using exactly the same options as described in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46b32df9b3eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.