# Issue

**Title:** add package info, command line entry point, and some initial docs

## Description

This PR adds basic usability and packaging to charcoal.

So, we can now do:

```
# install in developer mode from git repo
pip install -e .

# run!
charcoal run test-data/00-test.conf -j 12
```
addresses #27 
addresses #16

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a92a95ffe027`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.