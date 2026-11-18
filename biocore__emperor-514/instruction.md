# Issue

**Title:** Fix runner.js to execute tests correctly 🎉

## Description

The asynchronous nature of require.js lead to a problem where test suites would
not get executed. To fix this, I added all the dependencies to the first
execution of `require`, thus guaranteeing that all resources are available
before the tests begin executing.

As a consequence of all tests not being executed, I found a few failures
(nothing critical); these have now been fixed.

Finally, seems like with recent updates runner.js was producing some error
messages that would make the output of running the tests a bit misleading. I
have also fixed this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17341f90184b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.