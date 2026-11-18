# Issue

**Title:** Feat/delete data

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

I added a button in the settings for a user to delete all data, which seems to make logical sense. A dialog will render asking if a user is sure they want to delete. If they click yes, it deletes the observation file, all individual observation files, and clears the detailData and observations in the redux store.

This should satisfy the legal requirements that users can delete their data at any time.

### Test plan (required)

![gif](https://user-images.githubusercontent.com/47766436/79265590-55d3e180-7e64-11ea-9630-5f4089ec47d5.gif)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ x ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ x ] Have you added any new tests necessary?
- [ x ] Is your PR rebased off the most current master?
- [ x ] Have you squashed all commits, or if you will merge will you squash all commits?
- [ x ] Did you use yarn, not npm?
- [ x ] Did you use Material-UI wherever possible?
- [ x ] Did you format according to Prettier?
- [ x ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `381a76acb051`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.