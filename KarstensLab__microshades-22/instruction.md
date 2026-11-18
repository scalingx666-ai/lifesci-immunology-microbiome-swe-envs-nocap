# Issue

**Title:** Fix coercion of logical vector into length 1 error

## Description

Hi microshades team,


I changed the line of code that was causing issue #21 in new versions of R. I did this by checking if the number of `NA` values in `cdf$hex` or in `cdf$group` is greater than 0 (ie, if there are any NA values in either column). Is this the way it was intended to function?

Some details of why it's erroring are in #21 .

All tests still pass, microshades still works with my old version of R, and it's resolved the issue for my labmate who does have the new version of R. Please let me know if I should alter this in any way!

Thanks,
John

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f080297d719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.