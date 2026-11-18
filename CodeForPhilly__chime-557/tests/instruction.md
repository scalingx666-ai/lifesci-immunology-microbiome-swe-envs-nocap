# Issue

**Title:** 342 Adds lock zoom level [dash]

## Description

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

# Issue

- #342 

# Changelog entry

- Zoom Persists on parameter updates when the "Lock Zoom" button is in the on position
- The Lock Zoom Button is in the ON position by default.
- Removed "max_y_axis" feature

![image](https://user-images.githubusercontent.com/61572112/79602803-2c5fc380-80b9-11ea-9c76-228ea829ff59.png)

<p align="center">
  <img src="https://user-images.githubusercontent.com/61572112/79603264-fd961d00-80b9-11ea-9c74-f85798ed1ad8.png">
</p>

# Additional info

- This issue has not been completely fixed yet, need to update the streamlit app as well.

---

## <center>Pull Request Checklist</center>

### <center>For Reviewer</center>

- [ ] Submitted under the correct tag
- [ ] Runs without error or warning
- [ ] Documentation  revised / included
- [ ] Unit tests included
- [ ] Issues referenced
- [ ] Does not create new bugs / issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cecdd014015c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.