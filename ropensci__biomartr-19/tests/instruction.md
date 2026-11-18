# Issue

**Title:** modified DESCRIPTION, and added codemeta.json

## Description

- modified the DESCRIPTION file:
  - changed the "Author" format to the newer "Authors@R" format, eliminating the line for "Maintainer"
  - added isPartOf
  - added applicationCategory
  - added keywords, as advised by @HajkD 

used codemetar to write a codemeta.json file and add it.

/cc @cboettig

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e9837915cea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.