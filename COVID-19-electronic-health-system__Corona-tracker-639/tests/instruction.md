# Issue

**Title:** Fix bug: education cards cut off on smaller screens, issue #576

## Description

Fix bug where cards cut off on smaller screens

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

<!-- Please provide a basic summary of what this pull request fixes so that others can review it. -->
On smaller screens, the cards were cut off on the bottom. I have adjusted cards sizing for screens with a max width of 400 using Material UI theme.breakpoints.down(400). ## Details

<!-- Please explain the details for any changes. What existin problem does this pull request solve? -->

I picked 400 as it includes phones 6/7/8, and does not include Iphones 6/7/8plus. 

I also changed the Facts cards title style to match Quiz cards title, as on smaller screens the h4 font was too big compared to the body text size. 



## Test Plan (required)
I tested on Chrome console and my iPhone8. 

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->

## Final Checklist

- [x ] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [n/a] Did you add any new tests as necessary?
- [x ] Is your PR rebased off the most current master?
- [- ] Have you squashed all commits? _(can be done at merge)_
- [x] Did you use `yarn` not `npm`? _(important!)_
- [x] Did you use Material-UI wherever possible?
- [x] Did you run `yarn lint` on the code?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eac245fac120`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.