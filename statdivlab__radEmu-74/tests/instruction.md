# Issue

**Title:** Address issue #65 by checking for zero-comparison parameters and adding a flag

## Description

This PR addresses issue #65, which notes that sometimes we observe surprisingly small p-values in the "scientifically no signal" setting of having a categorical covariate with three or more levels, and testing a parameter that compares a covariate level to a reference level for a category in which both the comparison level and the reference level only have 0 counts for all samples. This PR does the following (so far in the limited setting when the model is fit with a single covariate):

- adds the function `zero_comparison_check()` which in the setting of a single categorical covariate with three or more levels, checks for these zero-comparison parameters, and if any are found produces a data.frame with covariate names, category names, and whether or not each parameter is a zero-comparison parameter
- calls `zero_comparison_check()` from `emuFit()` to check for these parameters, and if any exist, adds a column to the `coef` data frame that is returned called "zero_comparison" with this information
- adds the argument `remove_zero_comparison_pvals` to `emuFit()`, which can either be `TRUE` in which case all score test p-values associated with zero-comparison parameters are set to `NA`, `FALSE`, in which case no score test p-values associated with zero-comparison parameters are set to `NA`, or a value between 0 and 1, in which case all score test p-values from zero-comparison parameters that are less than the value are set to `NA`. Implements the results of this argument to all score test p-values returned in `coef` 
- tests these new functionalities in the file "test-zero_comparison_check.R" 

to-do: update this functionality to apply to an arbitrary design matrix, with any number of covariates

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea2cbbcf62f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.