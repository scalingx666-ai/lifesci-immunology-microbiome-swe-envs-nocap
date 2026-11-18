# Issue

**Title:** Couple things

## Description

Also, what do you think about setting the versions directly in the conda file e.g. rather than
```
concoct >= 1.1.0
```
have
```
concoct = 1.1.0
```
The advantage of that is that it means that if you know the version of Aviary that was run, you know the versions of each of the tools that you used, without having to inspect the conda envs directly.

Thoughts?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e557268c235f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.