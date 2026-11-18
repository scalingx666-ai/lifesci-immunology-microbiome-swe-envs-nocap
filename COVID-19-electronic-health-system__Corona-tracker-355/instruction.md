# Issue

**Title:** Stylize WeeklyTracker to near-final state

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

  

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

- Updates CSS so that weekly sliders are in a near-final state
- Implements `react-spring` as it's already being used in other places
- Removes `react-toastify` as it doesn't best fit our needs
- Moves logic of receiving and manipulating dates higher up in the DOM (HealthLog)

![ezgif com-video-to-gif](https://user-images.githubusercontent.com/15767602/78200830-d7d40b80-745d-11ea-9a12-7a33736e2eaf.gif)

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

**Need to add additional mock tests for all edge cases once we near our 4/15 deadline but have all necessary components ready**

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [x] Have you added any new tests necessary? **TODO add suite nearing 4/15**
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f109f472de6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.