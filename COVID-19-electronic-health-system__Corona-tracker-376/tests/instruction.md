# Issue

**Title:** HOTFIX: Fix `yarn.lock`s and calendar width

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

**HOTFIX - no issue**

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

- Added back the `yarn.lock` and removed the `yarn.lock` in the root directory
- Made calendar full screen width for aesthetics

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [x] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8822e6c3ce35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.