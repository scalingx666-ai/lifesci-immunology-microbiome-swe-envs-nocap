# Issue

**Title:** Create `main.yml`

## Description

Creates a script with GitHub Actions to automatically deploy our site to our QA S3 bucket

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an Issue first.__

All changes need to be discussed before proceeding. Failure to do so may result in the pull request being rejected.

Before submitting a pull request, please be sure to review:
- Our Code of Conduct: https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md
- Our Contributing Guidelines: https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md
- Our Support documentation: https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

Sets up continuous deployment to our QA S3 bucket

## Details

- Runs a GitHub actions script that deploys to our QA S3 bucket when code is merged into master
- Adds secrets to GitHub (AWS Credentials and bucket name)

## Test Plan (required)

Once this change merges in, we'll see if it automatically deploys 

## Final Checklist

- [x] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [x] Did you add any new tests as necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits? _(can be done at merge)_
- [x] Did you use `yarn` not `npm`? _(important!)_
- [x] Did you use Material-UI wherever possible?
- [x] Did you run `yarn lint` on the code?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `529778fd3749`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.