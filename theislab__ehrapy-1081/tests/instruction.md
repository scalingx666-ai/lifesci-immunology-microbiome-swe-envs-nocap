# Issue

**Title:** Maintenance: Improve fate tutorial robustness

## Description

<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

- [ ] This comment contains a description of changes (with reason)
- [ ] Referenced issue is linked
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] Documentation in `docs` is updated

**Description of changes**

CellRank v2.3.1  with numpy >= 2.4.x. This temporary fix should make the notebooks run until the next CellRank release

<!-- Please state what you've changed and how it might affect the user. -->

**Technical details**

<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. here. -->

**Additional context**

<!-- Add any other context or screenshots here. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef4d2d83edff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.