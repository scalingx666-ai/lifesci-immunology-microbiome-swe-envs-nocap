# Issue

**Title:** Add the ability to control multiple decomposition views

## Description

The main class, `EmperorController`, now has the ability to add additional `DecompositionView` objects. When a new object is added, a message is propagated to the controllers to refresh their metadata categories to include any new information.

Of note is that the metadata menu for controllers now include groups with the name of the decomposition view, and under that group, the metadata categories for that object.

These changes are a bit abstract, but I've commented (hopefully to make as readable as possible) the most esoteric sections.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3447ca06bc99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.