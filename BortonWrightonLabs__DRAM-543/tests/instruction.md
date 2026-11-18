# Issue

**Title:** feat: parse RGI output

## Description

-Parse RGI output to raw annotations file
-Update rules submodule to newest version
  -Add RGI annotations parsing to rules so rules can use RGI
  -Also newest version includes heatmap hover showing which gene_ids are present for for each rule

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4111ef394907`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.