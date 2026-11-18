# Issue

**Title:** Update `pyrodigal` to` v3.0`

## Description

Hi!

This PR updates the Pyrodigal annotation to use Pyrodigal 3.0 (which has bugfixes and more, but renamed the `OrfFinder` class to `GeneFinder` for consistency with the `find_genes` method).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13dd6c75f07a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.