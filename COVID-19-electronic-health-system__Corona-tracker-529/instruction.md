# Issue

**Title:** Refactors chart.jsx into rechart. Updates table to use stickyHeader.

## Description

Updates table to use stickyHeader. Removes classes to improve ui.
updates package.json

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:
I refactored the chart.jsx bar chart into a rechart line chart. I refactored the logic to make it more readable. 

Also added a stickyHeader tag onto table.jsx and removed the classes as they were messing up the margins and made the font look ugly in red. 

### Explain the **details** for making this change. What existing problem does the pull request solve?
The show me more page needed a facelift. 

### Test plan (required)
BEFORE:
<img width="1635" alt="Screen Shot 2020-04-16 at 10 45 10 AM" src="https://user-images.githubusercontent.com/53789410/79489938-ecbdac80-7fd0-11ea-8c9c-7d8c8ada1d21.png">
<img width="1631" alt="Screen Shot 2020-04-16 at 10 45 05 AM" src="https://user-images.githubusercontent.com/53789410/79489946-ef200680-7fd0-11ea-96c0-aea7c737c76c.png">

AFTER:

<img width="410" alt="Screen Shot 2020-04-16 at 10 42 43 AM" src="https://user-images.githubusercontent.com/53789410/79489969-f6471480-7fd0-11ea-9653-dd301f2e65ea.png">
<img width="395" alt="Screen Shot 2020-04-16 at 10 42 52 AM" src="https://user-images.githubusercontent.com/53789410/79489973-f810d800-7fd0-11ea-90ae-14bec4188886.png">
<img width="1660" alt="Screen Shot 2020-04-16 at 10 42 33 AM" src="https://user-images.githubusercontent.com/53789410/79489974-f8a96e80-7fd0-11ea-9ffc-e5012aa2445a.png">
<img width="1652" alt="Screen Shot 2020-04-16 at 10 42 28 AM" src="https://user-images.githubusercontent.com/53789410/79489978-f9da9b80-7fd0-11ea-8bc0-6e17681d7881.png">


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07557e31fd2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.