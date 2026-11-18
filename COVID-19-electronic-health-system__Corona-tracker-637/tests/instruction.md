# Issue

**Title:** Add language selector to settings

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

- Adds language selector to settings page
- Automatically updates language when navigating to other pages

## Details

<!-- Please explain the details for any changes. What existin problem does this pull request solve? -->

<img width="1382" alt="Screen Shot 2020-04-23 at 11 33 41 PM" src="https://user-images.githubusercontent.com/15767602/80172501-2ab36580-85bb-11ea-92ce-4573892c9c75.png">

## Test Plan (required)

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->

Not much to test here besides checking out the code and seeing

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db58276cbdf9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.