# Issue

**Title:** MAINT: `pkg_resources` deprecation

## Description

Replaces call to `pkg_resources` with the relevant `importlib` command.

We recently completed an org-wide sprint in QIIME 2 to remove all deprecated calls to `pkg_resources`. After completing this, I noticed there was still a deprecation warning within our latest QIIME 2 development environments:
```
/Users/elizabethgehret/miniconda3/envs/q2dev-amp/lib/python3.10/site-packages/emperor/__init__.py:9: UserWarning: pkg_resources is deprecated as an API.
See https://setuptools.pypa.io/en/latest/pkg_resources.html.
The pkg_resources package is slated for removal as early as 2025-11-30.
Refrain from using this package or pin to Setuptools<81.
```
Our next release is at the end of this month, so this change ensures continued compatibility post-release after `pkg_resources` is fully removed in November/December of this year.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `919d492f9bed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.