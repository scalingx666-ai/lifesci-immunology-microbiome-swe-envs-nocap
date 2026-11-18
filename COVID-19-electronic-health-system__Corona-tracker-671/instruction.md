# Issue

**Title:** Redux-subscribe

## Description

# ⚠️ __IMPORTANT: Please do not create a Pull Request without creating an issue first.__

All changes need to be discusssed before proceeding. Failure to do so may result in the pull request being rejected.

Please be sure to review our [Code of Conduct](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CODE_OF_CONDUCT.md), [Contributing Guidelines](https://github.com/COVID-19-electronic-health-system/.github/blob/master/CONTRIBUTING.md), and [Support documentation](https://github.com/COVID-19-electronic-health-system/.github/blob/master/SUPPORT.md) before submitting a pull request.

-----

## Please include the issue number the pull request fixes by replacing YOUR-ISSUE-HERE in the text below.

 

## Summary

Adds subscribed phone number state to onboard reducer.  Also error and success state for rendering snackbar dialogs.

New flow for subscribe action, to allow conditional rendering based on whether number is subscribed: Call subscribe/unsubscribe API.  Receive response.  If call succeeds, add/remove number from gaia, then add/remove it from redux store.  Update success state string (either "subscribed" or "unsubscribed") in store, triggering rendering of proper snackbar dialog.  If response fails, update error object in store, triggering error snackbar dialog.  On dialog close, clear error/success status in store.  Render subscribe/unsubscribe buttons based on existence of subscribedNumber state in redux store.

Fetch subscribed number on app load, add to Redux store.

## Details

This update allows for conditional rendering of subscribe/unsubscribe buttons and phone number input field, allowing the user to be sure whether they have successfully subscribed previously, and at which number.  Stops user from subscribing same number twice, or unsubscribing a number that isn't subscribed.  Also decouples async api calls and error handling from UI code.  

## Test Plan (required)

I have not written tests for this code.  I'm not well versed in testing and I don't really know how to approach testing this update, and I'm a bit busy.  If anyone wants to talk through that with me, I'd be happy to look at adding tests.  

![subscribe](https://user-images.githubusercontent.com/15807680/80646851-7d69a300-8a3b-11ea-9ccf-94a868ee205d.gif)


## Final Checklist

- [X ] For CoronaTracker, did you bump the version in `package.json`?
    - Update the second decimal for a major change
    - Update the third decimal for a minor change
    - Numbers can go past 9, e.g. `1.0.9` => `1.0.10`
    - For more info, read about [Semantic Versioning](https://semver.org/)
- [x] Did you add any new tests as necessary?
- [ X] Is your PR rebased off the most current master?
- [ ] Have you squashed all commits? _(can be done at merge)_
- [ X] Did you use `yarn` not `npm`? _(important!)_
- [ X] Did you use Material-UI wherever possible?
- [ X] Did you run `yarn lint` on the code?
- [X ] Did you run all of your most recent changes locally to make sure everything is working?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d6d2b280ee59`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.