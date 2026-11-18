# Issue

**Title:** get oneThird Value based off slider width instead of screen width

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:
1. Go to Calendar Page in screen sizes
-  screen size >= 839px 
-  screen size < 839px
2. Drag slider just past vertical line
3. See that the slider stays at the line

### Explain the **details** for making this change. What existing problem does the pull request solve?

The slider placement was being calculated based off the screen width and since the slider has a different view width for bigger views I decided to calculate the sliders placement based off the sliders width instead. Now when you go past the vertical line the slider stops at the vertical line.

### Test plan (required)
![slider](https://user-images.githubusercontent.com/53540583/79281059-0a2f3100-7e80-11ea-8ef1-f0e5d341a1ce.gif)


Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ ] Have you bumped the version in `package.json`?
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c98ee19567f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.