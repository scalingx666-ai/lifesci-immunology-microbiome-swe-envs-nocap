# Issue

**Title:** handle duplicate hashes in input cDBG.

## Description

It looks like #369 was caused by new consistency checks in our code that now check that two cDBG unitigs never share k-mer hashes. This could be due to a murmurhash hash collision (which happens, but should happen rarely) or due to a problem in the output cDBG (actual shared k-mers, which would be a bug). In this case, it's a hash collision. How exciting!

This PR addresses the issue by detecting and removing multicount hash values.

The effect of this fix is to simply ignore the (presumably extremely rare) hash values that have collisions. This means that they will present as k-mers missing from the data set. This should have approximately 0 effect on queries.

The impact on speed needs to be measured, as this adds conditionals that might be unfriendly. A better solution might be to implement this over in bbhash where we can take advantage of Cython...

Note that it's not clear bbhash is doing a sensible thing with duplicate hash values. Specifically, when we had dup hashvals in the list, it looks like bbhash did not detect this and would assign them different MPHF values, but only one of the values would be reachable. I need to confirm this behavior over in pybbhash, tho.

TODO:
- [x] verify that this is a duplicate k-mer hash with murmurhash, just 'cause
- [x] implement duplicate k-mer detection and removal
- [x] benchmark it.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9ae262a250f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.