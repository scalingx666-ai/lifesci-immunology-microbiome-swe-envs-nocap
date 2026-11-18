# Issue

**Title:** [FEATURE] make adaptive seeding available again

## Description

Making the internal search ourselves has quite positive effect on performance. 

Current version of adaptive seeding is very conservative and only brings 0-10% speed improvement (but it also doesn't make anything worse).

Splitting the translation units reduces compile time drastically again. Attention: if review the commits individually the diff is correct and shows files being renamed, but if you look at the total diff, it looks like huge copy'n'paste.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d54b0071c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.