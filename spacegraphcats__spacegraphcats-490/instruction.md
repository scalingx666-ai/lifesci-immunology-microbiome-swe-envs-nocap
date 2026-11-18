# Issue

**Title:** MRG: Ignore DeprecationWarning from sourmash in tests.

## Description

This fixes a test failure caused by sourmash:
```
DeprecationWarning: Deprecated call to `pkg_resources.declare_namespace('mpl_toolkits')`.
Implementing implicit namespace packages (as specified in PEP 420) is preferred to `pkg_resources.declare_namespace`. See https://setuptools.pypa.io/en/latest/references/keywords.html#keyword-namespace-packages
```
by turning off breaking errors for DeprecationWarning.

See  for further discussion.

First fixed over in genome-grist:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0384e6497939`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.