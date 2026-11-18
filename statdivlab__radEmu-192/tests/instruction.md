# Issue

**Title:** Closed-form Firth estimate for discrete designs; add estimates_only to emuFit

## Description

An initial attempt at #191 seems promising. 

With the help of my French RA, we

- derived closed form estimates for Firth penalized estimates in the 
- implemented them
- created a flag to return `estimates_only` -- **since this approach doesn't produce std errors** (they are not needed for the motivating example)

TODO(AW)

- [x] what is behaviour when X is cts and `estimates_only=TRUE`
- [x] full code review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4125fb228d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.