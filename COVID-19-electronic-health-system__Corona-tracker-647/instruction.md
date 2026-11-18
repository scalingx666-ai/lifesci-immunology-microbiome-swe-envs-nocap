# Issue

**Title:** Links to Terms and Conditions/Privacy Policy pages in Settings.jsx

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

<!-- Please provide a basic summary of what this pull request fixes so that others can review it. -->

Added Links to Terms & Conditions/Privacy Policy pages in Settings component at the very bottom.

## Details

<!-- Please explain the details for any changes. What existing problem does this pull request solve? -->

## Test Plan (required)

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->

Here is a gif showing it:

![Apr-25-2020 19-34-26](https://user-images.githubusercontent.com/53917594/80293422-450d5080-872d-11ea-9099-b943a2942940.gif)


## Final Checklist

- [X] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [X] Did you add any new tests as necessary?
- [X] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits? _(can be done at merge)_
- [X] Did you use `yarn` not `npm`? _(important!)_
- [X] Did you use Material-UI wherever possible?
- [X] Did you run `yarn lint` on the code?
- [X] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed9ab8974bee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.