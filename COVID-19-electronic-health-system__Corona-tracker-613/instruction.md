# Issue

**Title:** Fix Login component - infinite spinning on close Blockstack modal

## Description

### Please provide enough information so that others can review your pull request:

Add event listener `onPointerOver` for parent `div` element in `Login` component. On event function `closeModal` invokes and reset value of the `loginLoading` variable. Which prevent infinite loading spin when we close Blockstack modal without login in.

### Test plan (required)

![](https://media.giphy.com/media/kaUN3jqCPpWGeUbKOc/giphy.gif)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `258f12e2be63`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.