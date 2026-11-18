# Issue

**Title:** Update krakenuniq

## Description

Please note that the module changes are currently copied over from a module update that I'm trying to get merged  That needs to be reverted later and the module updated properly.

This PR changes some of the channel plumbing to introduce a prefix for each sequencing reads file (or pairs).

Some doubt remains about the use of `meta.id` as the prefix. I think, that refers to the sample identifier which may be non-unique if multiple runs are not merged. Potentially, that has to be changed to something else.

I have run a local test and it seems to address #533

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93aa4993d27b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.