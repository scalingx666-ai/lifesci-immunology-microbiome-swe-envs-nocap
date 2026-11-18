# Issue

**Title:** [MRG] add `defaults.conf`; update docs to specify YAML instead of JSON

## Description

This PR adds a `defaults.conf` and updates the docs in a few ways.

Goals:
* make it so that `showconf` target actually shows _all_ of the config options, not just the ones set in the config file
* provide reasonable (or empty) defaults, provide good error messages when required parameters are not set.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d0a2127a054e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.