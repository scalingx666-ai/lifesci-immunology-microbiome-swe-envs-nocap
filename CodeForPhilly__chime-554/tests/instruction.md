# Issue

**Title:** #358 Add tests for the cli

## Description

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

# Link to issue

Add tests for the cli
Fixes: #358

# Changelog entry
- Added unit tests to run simulation via CLI
  - Smoke test with doubling-time
  - Smoke test with date-first-hospitalized
  - Negative test if neither doubling-time nor date-first-hospitalized are defined
  - Integration test to run a five-day simulation and verify the results.

# Additional info

- Functionality of method main in module cli has been has been extracted to a method run in order to support testing by injecting custom arguments.
- The integration test uses the system date as current date and does not define the current-date argument. This is due to the fact that even with current-date the system date has an impact on the results.

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [ ] Submitted under the correct tag
- [x] Runs without error or warning
- [x] Documentation  revised / included
- [x] Unit tests included
- [x] Issues referenced
- [ ] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1295b2888dab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.