# Issue

**Title:** Allow skipping input sequences that are too short

## Description

Sometimes a sequence in an input dataset is too short; in particular, if it is shorter than the probe length, the `candidate_probes` module is unable to design candidate probes from it and raises an error. One way to fix this is with the existing `--small-seq-min` argument, which allows designing short probes against those sequences.

This argument provides another way to handle this: it allows the `candidate_probes` module to skip over sequences that are shorter than a specified value (typically the probe length minus 1). Note that it is possible that such sequences will not be covered in the design (i.e., if no other candidate probe covers them).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1484b41f9afe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.