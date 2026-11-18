# Issue

**Title:** ehrdata as submodule

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [x] This comment contains a description of changes (with reason)
- [ ] Referenced issue is linked
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Documentation in `docs` is updated

**Description of changes**

Add `ehrdata` as a submodule.

This allows to run ehrdata from its latest commit (or a commit from a branch during development) in the ehrapy CI.

The goal for this is to facilitate developing changes in ehrdata that might affect ehrapy.

<!-- Please state what you've changed and how it might affect the user. -->

**Technical details**

<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. here. -->

**Additional context**

<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `451b2535c107`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.