# Issue

**Title:** fix: no longer gen gff file, fixing dbcan output

## Description

DRAM no longer will try to generate a gff file from called genes. dbcan CGC needs a gff file, so called genes can't run CGC anymore, but by default we don't need CGC. Add option to save CGC output if users want it, but only run CAZyme Annotation normally, and fall back to CAZyme Annotation if users input called genes and try to save CGC.

antiSMASH can also not be ran with called genes anymore because it also needs a gff file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0320400cc6f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.