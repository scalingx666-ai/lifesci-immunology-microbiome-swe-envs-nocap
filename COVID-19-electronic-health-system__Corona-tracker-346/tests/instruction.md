# Issue

**Title:** Settings

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 and  

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

![settings](https://user-images.githubusercontent.com/55054963/78141932-7c3d5a00-742c-11ea-88b2-684feadaf901.gif)


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

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea85bb8911e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.