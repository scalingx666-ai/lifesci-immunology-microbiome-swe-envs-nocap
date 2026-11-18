# Issue

**Title:** Add skip local files functionality

## Description

The script will still collect up the full list of assemblies, but remove those that are already present on disk. It will now also check that the ftp and local files are the same size if there are files missing in each assembly version download.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d47b4e998388`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.