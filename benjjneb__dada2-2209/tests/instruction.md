# Issue

**Title:** Remove redundant -msse2 flag (fixes Windows ARM64 build)

## Description

`src/Makevars.win` passes `-msse2` unconditionally, which breaks the new Windows ARM64 (aarch64) toolchain:

https://github.com/r-universe/bioc/actions/runs/30404212773/job/90572895342

The flag turns out to be redundant on Windows anyway:

- The SSE2 intrinsics (`emmintrin.h`, `_mm_*`, `__m128i`) are all guarded by `#ifdef __x86_64` in `dada.h`/`kmers.cpp`, with scalar fallbacks otherwise — so they only compile on x86_64.
- On x86_64, SSE2 is part of the baseline ABI: the compiler enables it and defines `__SSE2__` by default, so `-msse2` is a no-op.
- On 32-bit x86 the intrinsics are compiled out entirely, so the flag does nothing useful there either.

So `-msse2` has no effect where SSE2 is actually used, and simply removing it fixes the aarch64 build.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72da7700b582`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.