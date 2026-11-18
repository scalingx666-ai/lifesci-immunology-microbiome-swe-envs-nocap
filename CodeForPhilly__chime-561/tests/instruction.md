# Issue

**Title:** #560 Limit forecasting window to one month

## Description

Limit forecasting window to one month #560
Setting "number of days to project" min is 1, max is 30

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

# Link to issue

- 

# Changelog entry

- Short description of problem & solution (1-3 sentences, depending on scope of change)
Setting the Min(1) and Max(30) numbers for "number of days to project" parameter

# Additional info

- Anything else reviewers and future readers should know

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [ ] Submitted under the correct tag
- [x] Runs without error or warning
- [x] Documentation  revised / included
- [x] Unit tests included
- [x] Issues referenced
- [x] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a8c569fccf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.