# Issue

**Title:** fixes: #386   Styling of Educate buttons

## Description

### Please provide enough information so that others can review your pull request:  Educate buttons reflect desired style.

### Explain the **details** for making this change. What existing problem does the pull request solve? #386 Educate button to look more like wireframes

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

Attached Screenshots
<img width="207" alt="Screen Shot 2020-04-05 at 1 37 38 PM" src="https://user-images.githubusercontent.com/47477912/78505828-03980f80-7744-11ea-944c-db6350939ac6.png">
<img width="415" alt="Screen Shot 2020-04-05 at 1 34 27 PM" src="https://user-images.githubusercontent.com/47477912/78505836-13afef00-7744-11ea-84c8-76fb41a5a135.png">



### Final Checklist

- [x ] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [ x] Is your PR rebased off the most current master?
- [ x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x ] Did you use yarn, not npm?
- [] Did you use Material-UI wherever possible?
- [x ] Did you format according to Prettier?
- [x ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f3298214866`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.