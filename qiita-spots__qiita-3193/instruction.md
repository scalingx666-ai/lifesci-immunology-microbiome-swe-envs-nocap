# Issue

**Title:** minimal fix for plugin testing

## Description

While developing new plugins, I noticed that once in a while some will not load correctly. After further investigation, it resulted that if the plugin relied on a plugin-type and the plugin-type had a filename that was alphanumerically higher than the plugin - the system reset will fail because the plugin-type will not be added before the plugin. 

This PR makes sure that plugin-types are always activated before regular plugins; solving the above issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0428d53912e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.