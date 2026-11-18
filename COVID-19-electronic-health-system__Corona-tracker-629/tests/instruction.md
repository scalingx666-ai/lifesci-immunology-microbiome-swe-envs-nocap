# Issue

**Title:** Refactor of the Table component

## Description

## Summary

- user can select charts with many records in the table

## Details

- Move charts checkboxes above table with survey results
- Move charts above table with survey results
- Adjust style of the charts container to fix gap between chart and table containers
- Add dynamic rendering of the charts and table of the survey results

## Test Plan (required)

- yarn start
- click `show me more`
- select `Fever` or `Behavioral` 

## Suggestion

I think that `show me more` view is overloaded with 2 charts and survey results table. I would suggest conditional rendering based on user selection. If user select fever chart, we can hide table to make view let over loaded with content. Open for dialog!  

## Final Checklist

- [x] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [x] Did you add any new tests as necessary?
- [x] Is your PR rebased off the most current master?
- [x] Have you squashed all commits? _(can be done at merge)_
- [x] Did you use `yarn` not `npm`? _(important!)_
- [x] Did you use Material-UI wherever possible?
- [x] Did you run `yarn lint` on the code?
- [x] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21c67b92d71f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.