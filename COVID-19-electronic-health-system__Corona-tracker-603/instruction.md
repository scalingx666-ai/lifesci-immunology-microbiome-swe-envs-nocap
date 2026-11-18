# Issue

**Title:** fixes #588: Prominent 'Get started' button

## Description

### Please provide enough information so that others can review your pull request:
Making get started button bigger/more prominent.

### Explain the **details** for making this change. What existing problem does the pull request solve? 
Used makeStyles object to enlarge button with css.

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

<img width="605" alt="Screen Shot 2020-04-20 at 3 34 40 PM" src="https://user-images.githubusercontent.com/47477912/79792370-c83d3980-831c-11ea-9bd8-561907369878.png">


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `748cb1793078`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.