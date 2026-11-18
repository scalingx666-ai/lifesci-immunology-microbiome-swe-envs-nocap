# Issue

**Title:** Atemp to create master json file for translations

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.



## Summary

Attempt to process json from Google docs API into languages master json file.

## Details

- Create `process_json.py` in `/src/python`. 
- Failed to update nested dictionary without rewriting it. Pair programming required or if someone can finish it!

Goal is to create json structured as `appText.json` created by @BrianHHough. It can be found here: `Translations/appText.json`.

## Test Plan (required)

<!-- Demonstrate the code is solid, e.g. list the exact commands you ran and their output, and screenshots/video if the pull request modifies the UI. -->

## Final Checklist

- [ ] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [ ] Did you add any new tests as necessary?
- [ ] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits? _(can be done at merge)_
- [ ] Did you use `yarn` not `npm`? _(important!)_
- [ ] Did you use Material-UI wherever possible?
- [ ] Did you run `yarn lint` on the code?
- [ ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73b46a2e563f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.