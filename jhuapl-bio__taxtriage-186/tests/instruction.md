# Issue

**Title:** code-agent-assisted commenting on section explanations since HTML is …

## Description

- code-agent-assisted commenting on section explanations since HTML is getting quite large (single file for simplicity to deploy in pipeline and GH pages)
- optimization steps for searching in MR html
- adding a hide/show all samples and allow it to be larger/smaller
- new scales to some tabs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13a1259aea06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.