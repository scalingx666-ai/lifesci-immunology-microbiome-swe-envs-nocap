# Issue

**Title:** Refactors male & female gender buttons into dropdown list

## Description

Refactors male & female gender buttons into dropdown list

Fixes mui components from overriding page css

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:
This fixes issue 470. Removes the Male and Female buttons and uses a muiSelect component instead. An extra gender "non-binary" has been added. 

The muiSelect component was using its own css instead of inheriting from the page (body) css. Therefore, I needed to override those css selectors in Layout.jsx. 

### Explain the **details** for making this change. What existing problem does the pull request solve?
We want to be more gender inclusive, and provide an easy way to extend to more genders in the future. The muiSelect component gives us that ability.

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.
Before: 
<img width="602" alt="Screen Shot 2020-04-12 at 2 02 03 PM" src="https://user-images.githubusercontent.com/53789410/79079828-43bc3c80-7cc6-11ea-9c0a-c4bf351fa4c0.png">
After: 
<img width="530" alt="Screen Shot 2020-04-12 at 2 01 41 PM" src="https://user-images.githubusercontent.com/53789410/79079836-4ae34a80-7cc6-11ea-812e-f506cbd2d4d5.png">
<img width="499" alt="Screen Shot 2020-04-12 at 2 03 20 PM" src="https://user-images.githubusercontent.com/53789410/79079860-651d2880-7cc6-11ea-8bb3-21028198cd83.png">


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78a67673b4e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.