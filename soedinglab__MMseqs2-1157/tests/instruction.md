# Issue

**Title:** Faster CPU ungapped prefilter

## Description

Signed 8-bit multi-column kernel for `UngappedAligner::score()`, plus dynamic scheduling and a per-thread top-N cut in `ungappedprefilter`. Results are byte-identical to master.

| | master | PR | speedup |
|---|---|---|---|
| aarch64 NEON (20 threads) | 103.2 s | 37.1 s | 2.8x |
| x86 SSE4.1 (Zen 5, 8 threads) | 167.8 s | 70.6 s | 2.4x |
| x86 AVX2 | 107.0 s | 48.0 s | 2.2x |
| x86 AVX-512 | 95.9 s | 43.2 s | 2.2x |

2M protein targets, 200 queries.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcf516aba34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.