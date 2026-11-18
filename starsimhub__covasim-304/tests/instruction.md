# Issue

**Title:** added blank lines to fix docs build break in people.infect docstring

## Description

The build on Read the Docs failed last night because the docstring for people.People.infect is missing some blank lines needed for correct formatting of the bulleted list.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b8f1dd052f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.