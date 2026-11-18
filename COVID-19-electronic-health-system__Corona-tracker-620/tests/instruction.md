# Issue

**Title:** Adding Dutch language to the app

## Description

### Please provide enough information so that others can review your pull request:

- Create directory for Dutch language `client/public/locales/nl` with `translation.json` in it with Dutch language content. 
- Add Dutch language to the constant.js

### Test plan (required)

yarn start
click on language select menu and pick Dutch

![](https://media.giphy.com/media/kBrV6QqQjaDwnhj2e3/giphy.gif)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e418f780d26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.