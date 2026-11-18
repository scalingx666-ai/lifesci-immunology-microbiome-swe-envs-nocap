# Issue

**Title:** Adapt to updated ed.infer_feature_type, discard alternative feature type inference used in some imputation methods

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [ ] This comment contains a description of changes (with reason)
- [x] Referenced issue is linked
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [x] Documentation in `docs` is updated

**Description of changes**



- Adjusts ehrapy to use `ed.infer_feature_types` everywhere:
 With this,  
  - `ed.infer_feature_types` is used now in `knn_impute`, `mice_forest_impute`, which before used another private ehrdata feature type inference method. This private ehrdata feature type inference method does not exist anymore.
  - `ed.infer_feature_types` now considers sequences of integers 0, ... , n as numeric, and not categorical. The expected behaviour in tests and use in tutorials is updated
 - Some polishments in the notebooks
 - The bias notebook is fixed and added again to the CI workflow.

<!-- Please state what you've changed and how it might affect the user. -->

**Technical details**

<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. here. -->

**Additional context**

<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe7ca592c2b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.