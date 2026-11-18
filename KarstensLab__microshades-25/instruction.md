# Issue

**Title:** Update prep_mdf to allow option to remove NAs

## Description

Hello!

As introduced and documented in issue #18 by @sterrettJD, currently in microshades relative abundances are calculated with NA values removed. This can affect interpretation of data, depending on the dataset being examined.

This pull request proposes a new parameter in the `prep_mdf` function, `remove_na`, that allows users to specify whether or not NA values should be removed during the taxa agglomeration step.

This parameter by default is FALSE, meaning that it *changes the current default behavior of microshades* such that NA values are **NOT removed** in the taxa agglomeration step.

The use of this parameter to remove NAs and how NA values can affect data interpretation (including visual comparisons) has been documented in a newly added vignette ["Remove NA Option"](https://github.com/anashen/microshades/blob/aa71fbf2c78e1e3b0deab44e4b8bdf298334f395/vignettes/remove_na_option.Rmd).

Thanks!

Anagha

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ba4ed132f90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.