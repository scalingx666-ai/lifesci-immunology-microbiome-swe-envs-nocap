# Issue

**Title:** Hide several less-used CLI options

## Description

Let's be real, what are the chances a Vamb user is going to experiment with tweaking alpha or the latent space size?
It's nice to have these flags when testing, but we don't need to display them in the help menu. All they do is confuse users and drown out the actually important parameters users need to set.

__For reviewers__: Please let me know if a) you agree these should be hidden for users, b) any more should be hidden (do we need to support `-ploss`? Should we just keep only the flat softmax?)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7dc2f98cd5f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.