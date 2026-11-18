# Issue

**Title:** survey displays if has not been submitted

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?
If the survey hasn't been submitted for the day, after logging in survey page will be rendered, otherwise the home page will be displayed. I am using window.localStorage to solve this problem, can add the code for it for browsers that don't support localStorage if necessary. 
### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.
Ran the app locally two days in a row, if the survey has not been submitted the first page the user will see after logging in will be the survey. If the user logs out and logs back in the same day the home page will be displayed.
<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [ ] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits, or if you will merge will you squash all commits?
- [ ] Did you use yarn, not npm?
- [ ] Did you use Material-UI wherever possible?
- [ ] Did you format according to Prettier?
- [ ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2764b5f89f28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.