# Issue

**Title:** Extend functionality of `show_simulation_step` parameter

## Description

The `show_simulation_step` parameter can now be used to specify the frequency of the output. E.g. setting `show_simulation_step = 200` yields the following output:

```bash
Time step: 0
Time step: 200
Time step: 400
Time step: 600
Time step: 800
Time step: 1000
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfceb3f3192a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.