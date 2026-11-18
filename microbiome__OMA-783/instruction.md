# Issue

**Title:** Add code styling to GHA

## Description

.

It's setup to have indentation of 4 spaces according to Bioconductor [guidelines](https://contributions.bioconductor.org/r-code.html#coding-style).

One point that is difficult to implement is 

* No space around “=” when using named arguments to functions. This: somefunc(a=1, b=2)

In `mia` this convention is [not followed strictly](https://github.com/microbiome/mia/blob/devel/R/runCCA.R#L356), so this current implementation should work?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3811391dfc9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.