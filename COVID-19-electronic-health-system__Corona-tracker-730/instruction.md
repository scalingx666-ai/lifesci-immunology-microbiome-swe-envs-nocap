# Issue

**Title:** add i18nkeys to layout components

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
Add translation to layout components
<!-- Please provide a basic summary of what this pull request fixes so that others can review it. -->

## Details

<!-- Please explain the details for any changes. What existing problem does this pull request solve? -->
![Screenshot 2020-06-12 at 08 45 19](https://user-images.githubusercontent.com/55054963/84473298-191c3f00-ac89-11ea-8d23-017ae635161c.png)

![Screenshot 2020-06-10 at 21 36 08](https://user-images.githubusercontent.com/55054963/84310910-b03aa700-ab62-11ea-8292-de0b3743c747.png)
![Screenshot 2020-06-10 at 21 35 33](https://user-images.githubusercontent.com/55054963/84310914-b2046a80-ab62-11ea-85d7-4d030c8c0ae2.png)

## Test Plan (required)

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->

## Final Checklist

- [x] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [ ] Did you add any new tests as necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits? _(can be done at merge)_
- [x] Did you use `yarn` not `npm`? _(important!)_
- [x] Did you use Material-UI wherever possible?
- [x] Did you run `yarn lint` on the code?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac209828240f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.