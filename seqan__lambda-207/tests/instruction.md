# Issue

**Title:** Add parameters for bisulfite profiles

## Description

This PR defines the parameters for the bisulfite default, fast and sensitive profiles.

I realized that we have no recommendations for E-value cut-offs anymore, now that we switched to the default bit score. Should we change that somehow?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df1c74dfe634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.