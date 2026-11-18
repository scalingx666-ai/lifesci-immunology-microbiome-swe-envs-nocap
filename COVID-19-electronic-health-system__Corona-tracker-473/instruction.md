# Issue

**Title:** FIX: Layout.jsx - fixed scrolling bug, issue#443

## Description

fixed scrolling behind cards on education screen by adding position fixed to layout and separating navbar and main layout into separate divs

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 



### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?



Hi, I made changes to Layout.jsx to fix the scrolling bug in issue #443. I made Layout root div have a fixed position and separated the main root background div and NavBar into separate divs. 
Tested on my Macbook Chrome browser and iPhone 8, All views look good on my end. When I move Education cards, the background stays put. I did not see anything brake on other views.

I was not sure if I need to bump the pachage.json version. Only saw that instruction after I submitted the PR. Let me know if I need to make any changes.

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f99eacd5aeb6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.