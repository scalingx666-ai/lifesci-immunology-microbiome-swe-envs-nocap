# Issue

**Title:** Avoid GCC 12 uninitialized warning in AVX512 hmax

## Description

## Summary

The `build-and-push-gpu-amd-image` job in the Docker workflow has been failing on `master`.
The CPU part of the ROCm image is built with Debian bookworm's GCC 12.2, with `-DENABLE_WERROR=1`.

GCC 12 reports a false positive there, and `-Werror` turns it into a build error:
```
FAILED: src/CMakeFiles/mmseqs-framework.dir/alignment/UngappedAlignerAVX512.cpp.o
/usr/lib/gcc/x86_64-linux-gnu/12/include/avx512fintrin.h:6012:10: error: '__Y' is used uninitialized [-Werror=uninitialized]
  inlined from 'uint8_t simdi8_hmax_avx512(__m512i)' at lib/simd/simd.h:126
  inlined from 'UngappedAVX512::signedScore(...)' at src/alignment/UngappedAlignerInternal.cpp:154
```

## Cause

In GCC 12's headers, `_mm512_extracti64x4_epi64` passes `_mm256_undefined_si256()` (written as `__m256i __Y = __Y;`) as its merge source. After inlining, GCC 12 warns that `__Y` is uninitialized. The code is correct.
The warning appeared after #1157 added `signedScore` as a new caller of `simdi8_hmax_avx512`.

`_mm512_castsi512_si256` doesn't avoid the problem either.
GCC 12 builds it on `_mm512_extractf64x4_pd`, which merges into an undefined value the same way.

## Change

`simdi8_hmax_avx512` now uses the full-mask zeroing extract for both halves:

```cpp
_mm512_maskz_extracti64x4_epi64(0xFF, buffer, 0)
_mm512_maskz_extracti64x4_epi64(0xFF, buffer, 1)
```

The mask selects all four 64-bit lanes, so the result is bit-identical to the unmasked extract.
The merge source becomes `_mm256_setzero_si256()`, which GCC doesn't warn about.
The intrinsic is AVX512F, which the enclosing `#ifdef AVX512` block already requires.

## Testing

- Reproduced
  - In a `debian:bookworm-slim` container with g++ 12.2.0-14+deb12u1, compiling `src/alignment/UngappedAlignerAVX512.cpp` with the CI flags fails on master with the four errors above.
- Fixed
  - The same compile succeeds with this change.
- Same machine code
  - GCC 12.2 and clang at `-O3` produce exactly the same instructions as before (no instruction for the low half, `vextracti64x4 $1` for the high half), so speed is unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d314d5ed7f86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.