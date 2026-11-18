# Issue

**Title:** Feat/back buttons

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

These changes add back buttons to SurveyPage2 and SurveyPage3. Navigating back and forth in the survey saves whatever data is filled out in the redux store. After completing a survey and sending the data to the database, the redux store clears for any subsequent survey attempts.
![gif](https://user-images.githubusercontent.com/47766436/78712616-df286880-78e6-11ea-9f8e-ea042ee323aa.gif)

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60230788a2c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.