# Issue

**Title:** Feat/add none buttons

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

<!-- Please provide a basic summary of what this pull request fixes so that others can review it. -->
Added none buttons to button-based survey questions

![Screen Shot 2020-04-22 at 5 15 04 PM](https://user-images.githubusercontent.com/12787123/80049282-704f3000-84e0-11ea-89c9-a0d575c2555b.png)
![Screen Shot 2020-04-22 at 5 16 17 PM](https://user-images.githubusercontent.com/12787123/80049283-71805d00-84e0-11ea-9377-2c9c9637850a.png)
![Screen Shot 2020-04-22 at 9 07 46 PM](https://user-images.githubusercontent.com/12787123/80049284-7218f380-84e0-11ea-8b65-d089a787a2ef.png)


## Details

<!-- Please explain the details for any changes. What existin problem does this pull request solve? -->

## Test Plan (required)

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->

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
- [ ] Did you run `yarn lint` on the code?
- [X] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44de194f5023`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.