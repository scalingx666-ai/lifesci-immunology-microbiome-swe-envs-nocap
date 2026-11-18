# Issue

**Title:** [FEATURE] re-activate bi-fm-index

## Description

This PR re-activates the BI-FM-Index. It contains a workaround for a build-failure in GCC7 ().

But at least on my systems, this still ICEs on GCC8 and GCC9. Can you verify this, @sarahet ?

I have reported this here: https://gcc.gnu.org/bugzilla/show_bug.cgi?id=92778

Some preliminary tests with bifm (using wavelet trees) are promising (20% raw speed-up, possibly more with different strategies).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `490bd5840200`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.