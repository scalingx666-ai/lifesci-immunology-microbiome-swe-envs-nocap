# Issue

**Title:** Gave classes.buttons in More component a minHeight of 50px to fix tex…

## Description

…t overflowing buttons

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

Added a minHeight of 50px

### Explain the **details** for making this change. What existing problem does the pull request solve?

 to fix text overflow in signout button in the more component

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

Works on both desktop:

![image](https://user-images.githubusercontent.com/36338290/79090496-e5b84500-7d17-11ea-9f25-15eb5fb3505e.png)

And on Android chrome(white spot is the keyboard, phones screenshot is a bit messed up):
![image](https://user-images.githubusercontent.com/36338290/79090939-5ca20d80-7d19-11ea-838b-fc9aa3068418.png)


<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [ ] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78a67673b4e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.