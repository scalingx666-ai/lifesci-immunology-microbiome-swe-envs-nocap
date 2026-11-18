# Issue

**Title:** BUG: Resolve stable URLs depending on package version

## Description

Deals with a problem where plots created with the `remote=True` argument would lead to the plots failing if new dependencies were added.

The base URL is now resolved depending on the version string. I had to change the tests because we can no longer test `remote=True` explicitly as the version string will change dependent of the version.

@wasade, this would deal with the need to update the figures in the deblur-manuscript repo.

------------

#### During code review this point came up

- [x] When `remote=True` is used, the code should raise a warning alerting the user of the possible consequences of these actions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `02e0292d9239`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.