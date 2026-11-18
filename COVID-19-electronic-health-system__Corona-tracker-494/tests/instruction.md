# Issue

**Title:** Removed react-with-gesture

## Description

### Please provide enough information so that others can review your pull request:

Ran yarn remove react-with-gesture

### Explain the **details** for making this change. What existing problem does the pull request solve?

To remove deprecated dependancy on react-with-gesture for focus on react-use-gesture

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

Sorry I didn't think to take a screenshot of the command output before running yarn run start to test. The output had some warnings but no errors. The fact that there are no changes in the package.json and yarn.lock files supports this. I also tested the drag gesture and it works both on my phone and on desktop. 
https://gyazo.com/e6279b18c09c3a2ac59753858f4c4983

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [x] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [ ] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcfe8a9a9631`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.