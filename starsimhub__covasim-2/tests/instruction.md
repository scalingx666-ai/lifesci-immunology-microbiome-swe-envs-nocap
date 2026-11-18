# Issue

**Title:** Optimize main loop

## Description

Quick optimization of main loop. Instead of iterating over susceptible people, filter them out and iterate over rest.

before
```
Total time: 6.63346 s
```

after
```
Total time: 4.81518 s
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a85f63e1722`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.