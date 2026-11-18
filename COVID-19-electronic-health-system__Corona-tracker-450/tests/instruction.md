# Issue

**Title:** Survey buttons

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

, 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

- Fixes button click bug on survey page 1 where button would not be highlighted after being clicked
- Button clicks on survey page 2 now do not alter their margins
- General survey style improvements for different window sizes

**Note on #444:** I could not reproduce the bug where buttons would not remain highlighted when scrolling on mobile. 

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

**#444**

![button-select-page-2](https://user-images.githubusercontent.com/16993949/78948358-fce80000-7a95-11ea-86ed-02a296a8aabc.gif)

**#445**

![button-select](https://user-images.githubusercontent.com/16993949/78948374-0709fe80-7a96-11ea-913f-16a97c3d5399.gif)


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab17bfc242ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.