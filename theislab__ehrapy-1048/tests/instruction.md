# Issue

**Title:** Discard the ML notebook from the documentation

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [x] This comment contains a description of changes (with reason)
- [ ] Referenced issue is linked N/A
- [ ] If you've fixed a bug or added code that should be tested, add tests! N/A
- [x] Documentation in `docs` is updated

**Description of changes**

The ehrdata submodule is updated to the latest ehrdata commit, which is also release 0.2.0.

The notebooks submodule is updated to discard the ML notebook in the documentation.
Here is [a link to the former notebook "Using ehrapy with machine learning"](https://github.com/theislab/ehrapy-tutorials/blob/8c972d1929d98ca70615dc18f0fd821a75b01833/ml_usecases.ipynb) for reference

<!-- Please state what you've changed and how it might affect the user. -->

**Technical details**

<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. here. -->

**Additional context**

<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb94a43dcab0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.