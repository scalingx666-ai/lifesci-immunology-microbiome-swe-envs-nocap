# Issue

**Title:** Add black to CI & project dependencies

## Description

Addresses issue 

This PR:
- Adds [`black`](https://github.com/psf/black)
- Adds a script `script/format` to run black on the correct files
- Runs black as a part of the `Lint and Test` workflow
  - It's set to `continue-on-error` in this PR, but in the future, when we're ready to format the whole codebase, we can remove this option so that future PRs won't pass CI until they're formatted correctly. 

<img width="929" alt="image" src="https://user-images.githubusercontent.com/20747904/78192071-5f615080-7445-11ea-9ecb-3825791d3d38.png">



Also, I noticed that `pytest` was in the `[dependencies]` section of the `Pipfile`, so when I added `black` to the dev dependencies, I moved `pytest` there was well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fbfb775d3f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.