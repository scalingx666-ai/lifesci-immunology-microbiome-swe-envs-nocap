# Issue

**Title:** fixed onboard textinputs

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:
### Explain the **details** for making this change. What existing problem does the pull request solve?
Was hard to tell if a field was a dropdown or a text input. Changed styling for inputs to be different from UI buttons. Made Placeholder for text input to say "Enter Age" etc. Made Age input a number input. 

### Test plan (required)
Go to Onboard page to see view.
1. Click More
2. Click Update Information

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

![Screen Shot 2020-04-20 at 1 57 53 PM](https://user-images.githubusercontent.com/53540583/79784176-e05a8c00-830f-11ea-9192-519635ff8fdf.png)


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1be53c78ba1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.