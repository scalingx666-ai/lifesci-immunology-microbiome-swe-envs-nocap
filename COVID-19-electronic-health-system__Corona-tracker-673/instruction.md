# Issue

**Title:** add indicator to swipe WeeklyTracker.jsx

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

Adds an indicator for the user to swipe WeeklyTracker.jsx 
## Test Plan (required)

![Screen Shot 2020-04-29 at 10 05 17 PM](https://user-images.githubusercontent.com/54862890/80664786-a56dfc00-8a65-11ea-90f7-bdbcfe64ec1a.png)


## Final Checklist

- [X ] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [X ] Did you add any new tests as necessary?
- [ X] Is your PR rebased off the most current master?
- [X ] Have you squashed all commits? _(can be done at merge)_
- [X ] Did you use `yarn` not `npm`? _(important!)_
- [X ] Did you use Material-UI wherever possible?
- [X ] Did you run `yarn lint` on the code?
- [X ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ae326ac2ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.