# Issue

**Title:** Reproducible, cross-platform --randseed for sintax, subsample and shuffle

## Description

Make the random-number-dependent commands produce identical output for a
given --randseed regardless of platform or thread count, and remove the
old C-library random() path.

- New reproducible-RNG facility in util.h/util.cc: SplitMix64, a 64-bit
  base seed (random_base_seed, no 32-bit truncation), and in-house
  random_bounded() (Lemire) / random_shuffle() (Fisher-Yates) instead of
  std::uniform_int_distribution / std::shuffle (implementation-defined).
- sintax: per-query SplitMix64 seeded from (base seed, query number) →
  --randseed reproducible regardless of --threads (was --threads 1 only).
- fastx_subsample: uniform selection via mt19937_64 + random_bounded
  (replacing the non-uniform overlapping-shift random_ulong).
- shuffle: portable Fisher-Yates seeded from the full 64-bit seed
  (replacing std::shuffle and the 32-bit seed truncation).
- Remove the now-unused random_int/random_ulong and arch_srandom/arch_random.
- Documentation updated in both manual systems (vsearch.1 and the
  per-command markdown manpages).

Note: the exact output for a given seed differs from previous releases
(the streams changed); reproducibility and statistical correctness are
preserved/improved.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed6919333e22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.