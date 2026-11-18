# Issue

**Title:** Query Gaia and Cleanup Logic

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

- Queries Gaia in `DiagnosticContainer`
- Sets the number of current queries in Redux
- Fixes `SymptomsTracker` to read from Redux store to get number of observations, abstracts away complexity farther down the DOM tree.
- Moved WeeklyTracker, Calendar into appropriate component

### Test plan (required)

TODO write a full suite of `DiagnosticContainer` unit tests

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [x] Have you added any new tests necessary? **TODO, larger issue**
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e2006617e3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.