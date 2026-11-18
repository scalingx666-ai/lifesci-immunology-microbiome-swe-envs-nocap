# Issue

**Title:** Dynamic viz params

## Description

This branch introduces dynamic, data-driven visual scaling for the anvi'o pangenome graph interactive display (anvi-display-pan). By replacing hard-coded values with values that scale with graph size, this update improves visualization consistency across a spectrum of genomic scales, from relatively large bacterial pangenomes to more compact mobile genetic element graphs.

**Comparison of UI figures before and after the changes**
A quick example
<img width="763" height="765" alt="Screenshot 2026-06-01 at 16 50 23" src="https://github.com/user-attachments/assets/ad65f4b3-f69c-4813-b7f3-5608e56b7f31" />

Please see this file for all comparisons
[dynamic-viz-params-fig-examples.pdf](https://github.com/user-attachments/files/28460034/dynamic-viz-params-fig-examples.pdf)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7c88f6ea973`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.