# Issue

**Title:** updated education quiz

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:
Changed wording of quiz section from False or True to "True or False" and changed swiping direction and instructions to match with the wording.


### Test plan (required)
Ran through the quiz to ensure functionality was still working.


<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
**Did not deem it necessary**
- [X] Have you added any new tests necessary?
- [X] Is your PR rebased off the most current master?
- [X] Have you squashed all commits, or if you will merge will you squash all commits?
- [X] Did you use yarn, not npm?
- [X] Did you use Material-UI wherever possible?
- [X] Did you format according to Prettier?
- [X] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6922733cd68a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.