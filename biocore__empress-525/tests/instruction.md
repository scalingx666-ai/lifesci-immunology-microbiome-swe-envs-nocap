# Issue

**Title:** Improves error handling when "shear" but no metadata passed

## Description

When `tree_plot` is run with `shear-to-feature-metadata`, but no metadata is passed, the following error is produced.
![image](https://user-images.githubusercontent.com/39198770/121439551-03446700-c93b-11eb-9928-376860fcc7d0.png)

This PR explicitly handles that case, improving the error message:
![image](https://user-images.githubusercontent.com/39198770/121439713-56b6b500-c93b-11eb-96c7-1b237b48de11.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c950cb462246`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.