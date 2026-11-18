# Issue

**Title:** fix crash when additional_params default is null in workflow params.json

## Description

Issue spotted by @ivagljiva.
Fixes a TypeError: argument of type 'NoneType' is not iterable crash when running workflows.
Since the workflow refactor moved defaults into per-workflow params.json, several additional_params entries were declared with "type": "str" but "default": null. That null flows into the config as Python None, and code that treats the value as a string crashes.

Solution: changed every null additional_params default to "".
Also: new guard/defense against a user who decided to put `null` instead of the new default `""` in read_recruitment/rules/main.smk, workflows/__init__.py and ecophylo/__init__.py.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f70d4b861d7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.