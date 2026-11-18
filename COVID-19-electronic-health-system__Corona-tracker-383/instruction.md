# Issue

**Title:** Add "Log My Health" slider

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

Creates the "Log My Health" slider, styled similarly to the wireframes, that takes the user to the survey page when it is swiped.

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

**Desktop**

![desktop-no-settings](https://user-images.githubusercontent.com/16993949/78466047-f559dd00-76ca-11ea-87d3-9eabd74624fa.png)

**Desktop with notification settings**

![desktop-settings](https://user-images.githubusercontent.com/16993949/78466050-fa1e9100-76ca-11ea-9069-4c9965348293.png)

**iPhone X**

![iphone-x-no-settings](https://user-images.githubusercontent.com/16993949/78466053-fc80eb00-76ca-11ea-99fb-e41738099ae4.png)

**iPhone X with notification settings**

![iphone-x-settings](https://user-images.githubusercontent.com/16993949/78466054-fe4aae80-76ca-11ea-87fd-de01d833f580.png)


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96b8e7bdb22d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.