# Issue

**Title:** Add "unknown" features to output of importMetaphlan

## Description

importMetaphlan imported only features with a known rank. However, sometimes Metaphlan do not detect a feature but just returns "UNKNOWN" (i.e., it does not have any rank). These features were dropped from the outputted TreeSE object.

This PR modifies the function so that the object includes also the unknown features.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95ee8b1c13c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.