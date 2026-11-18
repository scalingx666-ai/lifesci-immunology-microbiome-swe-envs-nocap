# Issue

**Title:** Fix a bug in cholmod that makes it do extra work

## Description

The cholmod solver path currently does extra work during the resistance shortcut mode. Prevent this from happening by modelling it like in the AMG solver path. Found after investigating why the cholmod wasn't scaling well in

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db991d287097`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.