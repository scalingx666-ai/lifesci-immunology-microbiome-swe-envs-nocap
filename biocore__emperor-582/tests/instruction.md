# Issue

**Title:** Update THREE.js to r83

## Description

Updates THREE.js and all plugins. Note that some of the require.js configs had to change due to some backwards incompatible changes in THREE, I opted for using the same strategy as \`ili as these changes are intended to allow the integration with `ili.

Note that we will want to update to the latest version r85 at some point, but this is good enough right now to allow testing with \`ili.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2d7302efdd4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.