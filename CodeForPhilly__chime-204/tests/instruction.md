# Issue

**Title:** Change projection days from a slider to a number input to allow larger max values

## Description

This PR changes the "Number of days to project" input from a slider to a number input. This allows users to set an exact value and to values greater than 200.

[Some context about slider vs input from Slack](https://codeforphilly.slack.com/archives/CV71EUYD8/p1584985223323200)



From comments, I also added to this PR to move the last few presentation UI elements to display in the sidebar and into the `Parameters` model.

Full screenshot of the changed UI.
![Screen Shot 2020-03-23 at 15 03 29](https://user-images.githubusercontent.com/153020/77353591-9d5cc700-6d17-11ea-96ee-958ee377cec3.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4177e463d87e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.