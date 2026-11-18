# Issue

**Title:** Fix --cluster-from-fragments bug with long fragment length

## Description

This fixes a bug in `genome.Genome.break_into_fragments()` when `--cluster-from-fragments` is specified with a `fragment_length` that is longer than the sequence length and `include_full_end` is True. In this case, `break_from_fragments()` ought to yield `seq` in its entirety. However, in this case, `len(seq)-fragment_length` is negative. `seq[len(seq)-fragment_length]` would pull out the last `len(seq)-fragment_length` nt of seq. If `fragment_length` is sufficiently long (>=2\*len(seq)), the result would be fine: it would yield `seq` in its entirety, as desired. However, if `fragment_length` is >len(seq) but <2\*len(seq), it would not yield all of `seq`.

This is meant to address Issue #37.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c8680620362`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.