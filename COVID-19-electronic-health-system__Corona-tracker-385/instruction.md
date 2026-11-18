# Issue

**Title:** Added about, onboard link, moved chart, fixed scrolling

## Description

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

- Adds `About` page with accomplishments and call to action
- Moves `Chart` into the `Show Me More` tab for aesthetics (can always remove)
- Makes app not horizontally scrollable to head rid of that headache
- Links buttons in `More` component to associated components
- Changes "Sex" to "Gender" in onboarding

![ezgif com-video-to-gif (1)](https://user-images.githubusercontent.com/15767602/78468265-24307d00-76e4-11ea-8e45-d093a784180d.gif)

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

- Added basic rendering test as everything else was already there and `About` is static

<!-- Make sure tests pass on both Travis and Circle CI. -->

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1a5654611a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.