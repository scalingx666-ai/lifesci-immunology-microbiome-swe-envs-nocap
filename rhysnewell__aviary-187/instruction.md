# Issue

**Title:** das_tool: Use script not shell.

## Description

Hey,

Basically converting the logic of the shell commands in the das_tool rule into a script, where a bit more care is taken.

There is a small functional difference. If a binning method has been run, but then rerun with that method in skip-binners. Previously bins from that binner were included, now they are not since the `Fasta_to_Scaffolds2Bin` script is only run for requested binners.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16e1c3eb599c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.