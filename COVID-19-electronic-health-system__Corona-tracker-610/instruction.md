# Issue

**Title:** Reversed map ordering of flashcards to reflect numbering

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

![image](https://user-images.githubusercontent.com/36338290/79817465-8a0f3c80-8353-11ea-82ff-e6e57fdadc6b.png)
Changed data={cardData[cardData.length - i - 1]} to data={cardData[i]} in FlashCards component

Also fixed fact numbers in fakeCardData.js

### Explain the **details** for making this change. What existing problem does the pull request solve?

Flashcards would show up in reverse order starting with fact 15 and going to fact 1

fakeCardData went 1,2,6,7,8,8 ... just fixed the numbering

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

![flashcards](https://user-images.githubusercontent.com/36338290/79829708-d0739400-8371-11ea-917a-4f92c50c34b4.gif)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18e1e24796b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.