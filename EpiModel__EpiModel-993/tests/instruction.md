# Issue

**Title:** Fix crosscheck stop gaps

## Description

## Summary

- Fix unreachable two-group parameter validation in `crosscheck.dcm()` where checks for `rec.rate.g2` and `r.num.g2` were nested inside blocks that `stop()` before reaching them
- Separate the `.g2` checks into their own `if` blocks so they execute when the base parameter is provided but the group 2 variant is missing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfdf868f18cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.