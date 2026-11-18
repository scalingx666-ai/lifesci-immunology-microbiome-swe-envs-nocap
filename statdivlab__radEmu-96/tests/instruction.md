# Issue

**Title:** Matching row names

## Description

This PR implements a process to ensure row names between covariate data and response data match when this information is available and provides helpful messages to the user indicating possible sources of inconsistencies, in order to address issue #94. The following checks are performed: 
**1.** If one or both matrices lack row names, but the number of rows is the same, then a one-to-one correspondence is assumed, but a message informing the user about this assumption is shown: "

> Row names are missing from (the matrix). Assuming a one-to-one correspondence with the rows of the (other matrix). Please double-check your data to confirm this correspondence."

 Message changes depending on which matrix is missing row names. 
If the number of rows does not coincide, an error message is printed instead: 

> "Row names are missing from the (matrix), and the number of rows does not match the number of rows in the (other matrix). Please check your data to resolve this inconsistency."

**2.** If both matrices have row names, then matching by row names is possible. A logical parameter `match_row_names` allows the user to disable this. 

**3.** If `match_row_names = TRUE` (default), we check first that no names are duplicated in any matrix (throwing an error message if we find duplicated names). Then, we subset to common row names with the following warning message if some row names did not coincide and thus were removed from the matrices 

> "Row names differ between the covariate matrix (X) and the response matrix (Y). Subsetting to common rows only, resulting in (number of rows preserved in both matrices) samples."

If all rows are common between the two matrices, but the order differs, we reorder X with the following message 

> There is a different row ordering between the covariate matrix (X) and the response matrix (Y). Covariate data will be reordered to match response data."

**4.** If `match_row_names = FALSE` we only check if the number of rows coincides between the two matrices, with the following error message if they do not

> "The number of rows does not match between the covariate matrix (X) and the response matrix (Y), and subsetting/matching by row name has been disabled. Please check your data to resolve this inconsistency."

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91336cfa0695`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.