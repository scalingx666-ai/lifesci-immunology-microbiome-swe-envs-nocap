# Issue

**Title:** Onboard form displays previous saved user data

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

Previously saved user data should be displayed as the default values on the user onboard form, rather than a blank form.

### Explain the **details** for making this change. What existing problem does the pull request solve?

Initial form state was previously hardcoded in onboard component.  Initial formstate in component is now the user's onboard data state mapped from redux store.  Initial state in the store updated to reflect the shape of a blank form.  Redux action changed to reflect fetching vs setting the user's onboard data.  Fetch action added to useEffect in App.jsx.

### Test plan (required)

![onboardform](https://user-images.githubusercontent.com/15807680/79587263-4640dc80-80a0-11ea-899c-ea016fbd8f6e.gif)

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [x] Have you added any new tests necessary?
- [X ] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits, or if you will merge will you squash all commits?
- [ X] Did you use yarn, not npm?
- [ X] Did you use Material-UI wherever possible?
- [ X] Did you format according to Prettier?
- [ X] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `461e4c4de72d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.