# Issue

**Title:** fixed more modal bug

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?
Clicking anywhere when modal was popped up closed it. This PR ensures that modal closes on a click outside of modal or on the buttons inside the modal.
Moved Dialog component outside of the Grid component which had the handleClickOpen function on it so since the Dialog was inside the modal was always closing on click since setOpen was being called with (!open) which means false so the modal closed. I also gave all the buttons inside the modal the handleClose func through onClick.

### Test plan (required)
1. Click on more
2. Click anywhere inside modal besides buttons, it wont close
3. Click either outside modal or one of the buttons inside modal, it will close
Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.
![moremodal](https://user-images.githubusercontent.com/53540583/79418418-975aae80-7f82-11ea-895c-abb11b615460.gif)


<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x] Did you use yarn, not npm?
- [x] Did you use Material-UI wherever possible?
- [x] Did you format according to Prettier?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34dac74fb4a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.