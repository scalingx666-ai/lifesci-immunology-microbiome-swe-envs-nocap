# Issue

**Title:** Fix text in CLI help

## Description

The help for the parameter `--ventilated-los` is `Hospitalized Length of Stay (days)`, which is a repeat of an another parameter descriptions and I think should say `Ventilated Length of Stay (days)`. If that's not the correct replacement text but it is in fact incorrect on master, let me know and I'll update the PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1ca63839dbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.