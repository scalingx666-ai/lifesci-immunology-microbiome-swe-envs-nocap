# Issue

**Title:** Survey2 buttons

## Description

## IMPORTANT: Please do not create a Pull Request without creating an issue first.

**Any change needs to be discussed before proceeding. Failure to do so may result in the rejection of the pull request.**

**Do not change the following line aside from replacing YOUR-ISSUE-HERE with the issue this PR fixes** 

 

### Please provide enough information so that others can review your pull request:

### Explain the **details** for making this change. What existing problem does the pull request solve?
Buttons would deselect in mobile browser. After inspecting it on mobile I found that the innerText obtained from clicking was different depending on where you clicked. If you log the e.target you'll see that clicking on the edge targets the button element but clicking in the middle targets the span element. So I inspected further and saw that the value for innerText were different, for the button it had a value of Minimal but with a new line vs the span where it has Minimal as we wanted. So when we do the ternary for determining a selected button it would be true if we clicked the middle but it would be false if we clicked the button. So instead I switched from using innerText to textContent so that either way the ternary would be true for clicking either. 


### Test plan (required)
1. Go on Mobile browser, and test it by purposely clicking the edge and watch it deselect after you click away. Pinch out to zoom in to accurately hit the outside.
2. Click the middle and you'll see it doesn't deselect. 

Clicking the outside gives you this:

<img width="990" alt="button" src="https://user-images.githubusercontent.com/53540583/79816713-db1e3100-8351-11ea-85e6-b5827ab85c7e.png">

Clicking Span gives you this:

<img width="986" alt="span" src="https://user-images.githubusercontent.com/53540583/79816680-ca6dbb00-8351-11ea-92b4-872debf8a7fa.png">
 
Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes UI.

Button textContent:

<img width="998" alt="button2" src="https://user-images.githubusercontent.com/53540583/79816958-613a7780-8352-11ea-9abb-73931a1dc83e.png">

Span textContent:

<img width="1006" alt="span2" src="https://user-images.githubusercontent.com/53540583/79816977-6992b280-8352-11ea-9f62-b04b470c4612.png">


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46c275b3cbbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.