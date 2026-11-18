# Issue

**Title:** Fix integer overflow when sizing the fastq_eestats2 count table

## Description

## Summary

In `--fastq_eestats2`, the per-(length-step, EE-cutoff) count table is sized with
`new_len_steps * opt_ee_cutoffs_count` and indexed with
`(x * opt_ee_cutoffs_count) + y`, both computed in `int` before being widened to
`size_t`. With a large `--length_cutoffs` range combined with many `--ee_cutoffs`
values the `int` product can overflow: the `resize()` then wraps to a small (or
huge) value and the indices wrap independently, allowing out-of-bounds writes
into the vector.

## Fix

Widen each operand to `size_t` before the multiplication, so the table is both
sized and addressed in 64-bit arithmetic. Output is unchanged for all realistic
inputs; only the overflow edge is affected.

## Testing

Default and `-Wconversion`/`-Wsign-conversion` debug builds are clean;
`--fastq_eestats2` with `--length_cutoffs`/`--ee_cutoffs` produces correct
output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c344570fca3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.