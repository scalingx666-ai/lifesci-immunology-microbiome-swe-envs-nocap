# Issue

**Title:** uncollapse by double click

## Description

Crude method to uncollapse clades by double clicking on them. The main goal of this pr was to allow users to uncollapse clades so that figure 2a can be recreated. This PR does NOT support the ability to recollapse the clade. The only way to recollapse is by toggling the "collapse clade" check box. However, this pr does set up the basic frame work and can be extended to support more complex operations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b5152947d62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.