# Issue

**Title:** Charts development

## Description

I intend to reuse Chart.js component for all types of Charts we need. Chart component render chart type based on the  ```chartType``` props we sending to it.

### Please provide enough information so that others can review your pull request:

- moved dummy data for Chart component from the ```rootReducer``` to the ```temperatureReducer```. 
- wired ```temperatureReducer``` with Chart component
- created ```chartType.js``` in the utils directory to store strings of the ```Chart.js``` types
- modify tests for Chart component to unsure that new reducer working and also to incorporate ```PropTypes``` check. 

Line:
![test](https://i.ibb.co/Dkm4f5V/Screen-Shot-2020-04-02-at-1-06-14-PM.png)

Bars:
![test](https://i.ibb.co/gm4YvH9/Screen-Shot-2020-04-02-at-1-11-13-PM.png)

### Test plan (required)

yarn test

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5accf15c6a25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.