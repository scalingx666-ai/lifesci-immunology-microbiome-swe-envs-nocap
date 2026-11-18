# Issue

**Title:** Initialise applyByModule

## Description

Hi!

This PR introduces the `applyByModule` function which provides a way to perform module-wise aka group-wise operations and analyses. Check `?applyByModule` for a few example uses.

It's still a draft, but we can discuss here:
- if current implementation looks good
- if mia vs ariadne is the right place to have it
- if name sounds good (applyByGroup and agglomerateByGroup are also nice though)

Cheers,
Giulio

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cba739c5561`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.