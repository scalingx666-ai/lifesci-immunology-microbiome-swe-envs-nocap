# Issue

**Title:** Pharokka1.3.1

## Description

adds ability in pharokka_plotter.py to plot tRNA, CRISPR, tmRNA.

Also adds -s in pharokka itself, will output separate single fastas, gff and genbank files along with -m - ideally used for situations where you have bulk phage isolates you want to annotate

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c822b4c3b8cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.