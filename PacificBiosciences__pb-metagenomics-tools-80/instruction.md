# Issue

**Title:** Filter superbins

## Description

Identifies superbins output from SemiBin2, which are >100 Mb in size. Including very large superbins (~1GB) will cause crashes in DAS_Tool. This new identification step will move all superbins to a superbin folder in the SemiBin2 output directory. These bins can be inspected to determine their contents, which can sometimes contain interesting eukaryotic genomes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9a88ba4f15b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.