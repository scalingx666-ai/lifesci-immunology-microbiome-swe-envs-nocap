# Issue

**Title:** fixes: #343 Calendar looks more like wireframes

## Description

### Please provide enough information so that others can review your pull request:
I've styled the calendar so the text is white and the background is a gradient darkblue => blue

### Explain the **details** for making this change. What existing problem does the pull request solve?  
The way I did this was by importing the react-calendar module main CSS file called Calendar.css and make the changes there. This CSS file is now located in ```/client/src/css/Calendar.css```

### Test plan (required)

Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.
Screenshot attached
<img width="450" alt="Screen Shot 2020-04-04 at 3 58 32 PM" src="https://user-images.githubusercontent.com/47477912/78460401-a1310780-768e-11ea-9d5d-d112e35762d0.png">

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [ x] Have you bumped the version in `package.json`?
    - Second decimal for major change, third decimal for minor change. This can go past 10 i.e. 1.0.9 !=> 1.1.0, 1.0.9 => 1.0.10
    - [Read here for more info](https://semver.org/)
- [ ] Have you added any new tests necessary?
- [x ] Is your PR rebased off the most current master?
- [ x] Have you squashed all commits, or if you will merge will you squash all commits?
- [x ] Did you use yarn, not npm?
- [x ] Did you use Material-UI wherever possible?
- [x ] Did you format according to Prettier?
- [x ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `daaa5c664eaa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.