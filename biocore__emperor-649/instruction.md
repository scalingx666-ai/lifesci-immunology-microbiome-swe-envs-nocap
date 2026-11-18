# Issue

**Title:** BUG: Prevent input propagation in the notebook 📓

## Description

The text inputs in the color picker propagated the keypress and keydown
events all the way down to the notebook. In the case where the inputs
conflicted with a shortcut in the notebook, the shortcut itself would be
triggered.

This has been fixed by preventing the propagation of events in all the
color pickers.

Thanks to @JWDebelius for reporting this bug. 👍

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45b1437c9e5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.