# Issue

**Title:** Added Behavioral Chart to Table.jsx and SurveyPage4.jsx

## Description

### Please provide enough information so that others can review your pull request:

Added the behavioral chart in SurveyPage4.jsx and Table.jsx 
Added checkboxes in Table.jsx for rendering Fever Chart and/or Behavioral Chart

### Test plan (required)
Please find the gif [here](https://im6.ezgif.com/tmp/ezgif-6-b55c56a8ee47.gif). 
The next step would be for @kevin-Price to advise on the Fever Chart, possibly another PR to convert the existing code on his repo mentioned in #370 

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a27934ffbf2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.