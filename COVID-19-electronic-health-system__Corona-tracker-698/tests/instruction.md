# Issue

**Title:** automatically open observation detail when there is only one observation

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an Issue first.__

All changes need to be discussed before proceeding. Failure to do so may result in the pull request being rejected.

Before submitting a pull request, please be sure to review:
- Our Code of Conduct: https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md
- Our Contributing Guidelines: https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md
- Our Support documentation: https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

When there is only one observation, the observation details will automatically open.

## Test Plan (required)


![Screen Shot 2020-05-09 at 4 44 06 PM](https://user-images.githubusercontent.com/54862890/81484568-646ba980-9214-11ea-8f59-a275c1769501.png)


## Final Checklist

- [ x] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [ x] Did you add any new tests as necessary?
- [x ] Is your PR rebased off the most current master?
- [x ] Have you squashed all commits? _(can be done at merge)_
- [x ] Did you use `yarn` not `npm`? _(important!)_
- [x ] Did you use Material-UI wherever possible?
- [ x] Did you run `yarn lint` on the code?
- [x ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1872b13d7470`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.