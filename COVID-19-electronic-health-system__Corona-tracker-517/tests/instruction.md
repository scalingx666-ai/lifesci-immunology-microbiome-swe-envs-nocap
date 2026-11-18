# Issue

**Title:** More fix

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 



### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?
1- removed `BottomNavigationAction` from `NavBar.jsx`
2- Adjusted `More.jsx` to fit style
### Test plan (required)
![more](https://user-images.githubusercontent.com/55054963/79396633-a3dc0880-7f7c-11ea-8a2c-7701526a3f6c.gif)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d926778a5b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.