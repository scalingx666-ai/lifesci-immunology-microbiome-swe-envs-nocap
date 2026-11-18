# Issue

**Title:** Feature/global genome size correction

## Description

This PR changes the abundance correction step in `ganon report`. The correction is no longer rank-based, but global. This simplifies the code and solves some inconsistencies and edge cases.

In practice, most results will remain the same since in general all reads are classified (or re-assigned) to the leaves of the tree, and those are usually at the same level (e.g. species). This change affects mostly results were the database have different targets ranks.

reads assigned to targets without proper genome size (`1`), are now using the closest parent node with a valid genome size for correction.

A new parameter was added `--ranks-abundance` that enable skipping of certain ranks that may shift genome size correction, for example: plasmids in a sub-species rank with very small genome size may get over-estimates if their genome size is used for correction. Using `--ranks-abundance species` (or to be complete in case of targets spread over the taxonomy `--ranks-abundance domain phylum class order family genus species`) all not-specified target ranks will use the closest parent values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8e9dd1e5a1a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.