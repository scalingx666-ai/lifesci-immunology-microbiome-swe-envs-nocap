# Issue

**Title:** Fix update-related issues

## Description

Hello! Here is an overview of the changes proposed in this pull request:

# Changes proposed

## 1) Replace use of the deprecated function `fct_explicit_na`. 
*Why*: Updating R results in an deprecated function error where `fct_explicit_na` is used, as documented in #19. 

*Fix*: Replace `fct_explicit_na` with `fct_na_value_to_level`.

## 2) Replace use of the deprecated function `aes_string`.
*Why*: `aes_string` was deprecated in a recent version of `ggplot`. 

*Fix*: Use the `.data` pronoun in the `aes` function where the aesthetics are specified in `ggplot` commands in the plot and legend functions.

## 3) Fix problems with use of external vectors in selecting functions.
*Why*: Using an external vector in selections was deprecated in a recent version of `tidyselect`.

*Fix*: Use `all_of` where vectors are used in the`select` function; replace input in the `group_by_at` function with a character vector of column names.

## 4) Update package dependencies in vignettes. 
*Why*: Packages `forcats` and `tidyverse` are required to be loaded in order for the Global Patterns Data and Human Microbiome Project 1 & 2 vignettes to run.

*Fix:* Add the necessary package load commands in the vignettes that require them.

- - -

Additionally: add a param comment to document recently added as_relative_abundance parameter in the `prep_mdf` function.

# Checks

- [x] Vignettes result in the same output with no changes.
- [x] No new warnings or errors have been generated.

Thank you!

Best,
Anagha

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f080297d719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.