# Issue

**Title:** Bits2

## Description

We don't have tests on this branch, but I have done some local tests that all look fine.

To use a minimum bit-score and no e-value, add `--e-value 100 --bit-score 42`.

@sarahet Can you run the following on a uniref DB and one small query file (maybe just 5 or 10MB):

1) lambda2 master branch with e-value 1e-4, one thread
2) this branch with e-value 1-e4, one thread
3) this branch with bit-score 60, one thread

The output of 1) and 2) should be identical. When filtering 1) for bitscore 60, the output should be very similar to 3 (ideally identical).
(This doesn't have to be on our benchmark server)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc636ea89eb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.