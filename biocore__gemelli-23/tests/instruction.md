# Issue

**Title:** fix dist build

## Description

The previous PR #22 for issue #21  fixed the dist build but not the pip. Forgot to add this to setup.py

```python
'gemelli': ['citations.bib']
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec2c23177a67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.