# Issue

**Title:** Add "Export to Excel" Button

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

Added "Export to Excel" button in Table.jsx


## Test Plan (required)

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->


![Screen Shot 2020-04-22 at 7 42 03 PM](https://user-images.githubusercontent.com/54862890/80044212-cc5e8800-84d1-11ea-93f7-8872ef2b197f.png)

# Final Checklist

- [ x] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [x ] Did you add any new tests as necessary?
- [x ] Is your PR rebased off the most current master?
- [x ] Have you squashed all commits? _(can be done at merge)_
- [x ] Did you use `yarn` not `npm`? _(important!)_
- [ x] Did you use Material-UI wherever possible?
- [x ] Did you run `yarn lint` on the code?
- [ x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e3f0928cc5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.