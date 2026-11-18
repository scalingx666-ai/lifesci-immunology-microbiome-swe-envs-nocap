# Issue

**Title:** Redirect to onboard screen on disclaimer agree

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 



### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?

After agreeing to the disclaimer, the user will now be redirected to the onboarding screen. This creates a more appropriate flow that encourages the user to input their information as soon as possible.

Previously, the disclaimer modal would only appear on the Log screen if the user had not seen it before, but not necessarily agreed to it. Now, the disclaimer modal appears on any screen after logging in, and will only disappear after the user agrees to it. This will help ensure that the user agrees to the disclaimer before using any part of the app.

### Test plan (required)

To test locally:
1. Create a new account, or use an account that has not agreed or disagreed to the disclaimer.
2. Navigate to any page by typing the URL manually (http://localhost:3000/, http://localhost:3000/education, etc.). The disclaimer modal should appear.
3. Click the disagree button for the disclaimer. The disclaimer modal should not disappear.
4. Refresh the page. The disclaimer modal should appear.
5. Click the agree button for the disclaimer. The disclaimer modal should disappear and the onboarding screen should be navigated to automatically.
6. Refresh the page now. The disclaimer modal should not appear.

<!-- Make sure tests pass on both Travis and Circle CI. -->

### Final Checklist

- [x] Have you bumped the version in `package.json`?
    - *I feel second decimal should be for minor change, and third for patch/bug fix, but I followed the recommendation below.*
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eff8185dbab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.