# Issue

**Title:** Adds callbacks to all controllers and documentation on how to use them

## Description

This is useful for the ongoing integration effort with Empress. In a conversation with @antgonza he suggested it would be useful to receive callbacks to the users double-clicking a category in Emperor. I implemented this using SlickGrid's events and THREE's event dispatcher objects.

Documentation looks like this:
<img width="1576" alt="Screen Shot 2020-06-15 at 6 16 58 PM" src="https://user-images.githubusercontent.com/375307/84721093-b0f18580-af34-11ea-8bea-e5e0e2362459.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5388392e3608`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.