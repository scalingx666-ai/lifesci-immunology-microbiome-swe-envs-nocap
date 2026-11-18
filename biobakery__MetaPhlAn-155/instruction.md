# Issue

**Title:** v3.0.12 alpha, unknown estimate changes

## Description

Here are a few proposed changes to implement Eric's rpks_any method for the unknown estimate. The final small change uses the kingdom level nodes for computing the estimate instead of those at the species level (which mainly changes the estimate for genome length).

All changes use the existing framework to try to be as modular and reusable as possible going forward. For efficiency we could add a conditional so the unknown estimate TaxTree is not created/computed if the unknown estimate is not requested by the user but I think this should only reduce the compute time by a few minutes. 

There are no changes to the core relative abundance calculation. This has been tested and confirmed. The final relative abundance outputs are changed only due to the change in the fraction of mapped reads. This change is required so that the abundances and the unknown estimate sum to 100.

Changes:
* Roll back to v3.0.9 unknown estimate and relative abundance calculation
* Remove trimming of markers by quantiles
* Change genome length to use median and add boost to length of 1.05
* Check and address corner cases (negative and zero)
* Change unknown estimate from species to kingdom level

Please reach out to me here or on slack with any questions or any changes you would like me to make.

Thank you,
Lauren

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b8cc9542aad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.