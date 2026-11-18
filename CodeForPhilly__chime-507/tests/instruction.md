# Issue

**Title:** [dash] Add default debounce argument for forms

## Description

I have added the `debounce` keyword argument to the `create_number_input` method which creates number inputs for the dash app. This causes the web widgets to call the callback only when either the input is unfocused or enter is pressed. Thus we have a smoother user experience.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb908cc8472a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.