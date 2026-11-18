# Issue

**Title:** Update qc_lab_measurements function

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [ ] This comment contains a description of changes (with reason)
- [ ] Referenced issue is linked N/A
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] Documentation in `docs` is updated

**Description of changes**

 updated the tests outlineing a new lab_qc_metrics functionality.

Currently, these tests fail

This PR

- Reverse-engineers the lab_qc_metrics function from the tests
- Renames `vars` to `var_names` as argument to avoid shadowing of `vars`

<!-- Please state what you've changed and how it might affect the user. -->



<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. here. -->



<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `213670edaa5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.