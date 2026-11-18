# Issue

**Title:** Regularization of covariance matrix by winsorizing the eigenvalues

## Description

This commit includes regularization of covariance matrix. The function "regularize_eigenvalues" was added to utils.R This function winsorizes very small eigenvalues to a value between 0.1-1. This value is chosen based on the ratio of eigenvalues to the largest eigenvalue. Using this function, the covariance matrix is regularized at lines 80-104 of the script sparse_linear.R. The regularized covariance matrix is returned as a stand-alone output and is included in the list of outputs at line 157.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74a695885cc1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.