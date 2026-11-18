# Issue

**Title:** ShareButtons component

## Description

### Please provide enough information so that others can review your pull request:

- Create ShareButtons component with [react-share](https://github.com/nygardk/react-share#readme) library
- Create basic test for ShareButtons component

@BrianHHough We going to need to add template of the message for share and hashtags for some of the social networks. More social networks can be added if needed.

@AdhamAH We need to make a decision where to place this component.

### Test plan (required)

![](https://media.giphy.com/media/kaZLMuZgPWNLSu1qZr/giphy.gif)

yarn test

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65b5cc1f8d3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.