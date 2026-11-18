# Issue

**Title:** More testing and refactoring, esp of clean_genome!

## Description

This does a lot of spot checking to make sure the numbers coming out of clean genome are not obviously wrong.

- [x] try filling in override field, instead of replacing filter_at directly
- [x] directly check values in the hit list against values emerging from clean_genome

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `877cdf517431`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.