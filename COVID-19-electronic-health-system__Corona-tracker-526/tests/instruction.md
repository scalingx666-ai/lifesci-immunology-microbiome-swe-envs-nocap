# Issue

**Title:** Hotfix - add @babel/compat-data and fix path to the logo image in README.md

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

fixes #YOUR-ISSUE-HERE

### Please provide enough information so that others can review your pull request

Hotfix - update of path to the logo image in the README.md
Hotfix - add @babel/compat-data to the pachage.json

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [ ] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits, or if you will merge will you squash all commits?
- [ ] Did you use yarn, not npm?
- [ ] Did you use Material-UI wherever possible?
- [ ] Did you format according to Prettier?
- [ ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed14b6e624c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.