# Issue

**Title:** Add i18n function and Japanese resource to streamlit chime

## Description

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

### Link to issue
- No related issues. This is individual PR.

### Changelog entry
- Add i18n feature to streamlit-version of CHIME, with Japanese resource.
   To realize this, add python-i18n to dependencies.

### Additional info
- I know dash-version CHIME has i18n feature, so I will contribute to dash-version by adding Japanese resources later.
  But, I feel some performance issues for the dash-version, so I want to have Japanese version of streamlit CHIME.
  So I add i18n feature and Japanese resource to it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbafcdd4e027`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.