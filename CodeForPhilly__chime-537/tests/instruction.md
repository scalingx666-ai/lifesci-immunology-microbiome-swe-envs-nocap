# Issue

**Title:** [DevOps] Update google-api-sheets to file based from env based.

## Description

<!-- Please read the contributing guidelines before submitting: https://codeforphilly.github.io/chime/CONTRIBUTING.html -->

<!--
- If this PR affects devops or model, start your PR title with `[DevOps]` or `[Model]`
- Update the user or developer documentation, if affected.
-->

### Link to issue
-  

### Changelog entry
- Using the `env` isnt friendly with the gspread api service from Google. Adjusting to pickup the file in its entirety. This PR goes with #536 

### Additional info
- Preprod and Production have the secrets applied. Tested in pre-prod with `chime-test` namespace and deployment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f884ba97fce8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.