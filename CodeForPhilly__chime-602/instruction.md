# Issue

**Title:** Fix Conflict

## Description

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

# Link to Problem

- Fixes Conflict with "Update sidebar.py" in cbafcdd4e0274e577adf61dd6346b7eefec845a8

# Changelog entry

- Resolved conflict, removed line 102 in sidebar.py, This line raised an error when launching the dash app, as the max_y_axis feature had already been removed.


---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [x] Submitted under the correct tag
- [ ] Runs without error or warning
- [ ] Documentation  revised / included
- [ ] Unit tests included
- [x] Issues referenced
- [x] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1771028d5314`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.