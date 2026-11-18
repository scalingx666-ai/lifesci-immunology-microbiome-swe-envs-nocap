# Issue

**Title:** Refactor Calendar component with react-calendar library

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

- Refactor Calendar.jsx component with using ract-calendar library
- Remove all references of the FullCalendar from Calendar Component
- Remove FullCalendar reference from package.json
- Render AppCalendar component in the DiagnosticContainer.jsx component
- Component connect to the redux and able to pass selected date to the redux action and use it for request to the backend.

### Explain the **details** for making this change. What existing problem does the pull request solve?

Refactor Calendar component.

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
- [ ] Did you format according to Prettier?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08c84f6804e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.