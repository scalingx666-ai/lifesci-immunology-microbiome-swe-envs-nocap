# Issue

**Title:** #353 Adds Log Scale Checkbox in Sidebar

## Description

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

# Link to issue

-  

# Changelog entry

- Added a checkbox in the sidebar to toggle between log scale and linear scale on all charts.
- Updated chart creation code to toggle between log scale and linear scale. Some adjustments to the input data to the chart were needed, because a y value of zero on the chart when using log scale causes it to glitch horribly.
- Updated parameters so that `--use-log-scale` can be passed in from the command line. 

# Additional info

- I noticed some missing and unclear documentation, so I added doc tags where appropriate. I'm sorry if this made the pull request bigger than expected. Just trying to keep things tidy!

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [X] Submitted under the correct tag
- [ ] Runs without error or warning
   - There are still JavaScript warnings in the console, but they appear to be happening on the develop branch as well. Should I be worried?
- [ ] Documentation  revised / included
   - Does anyone know how I would update the user documentation?
- [X] Unit tests included
- [X] Issues referenced
- [X] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45aeb494a7bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.