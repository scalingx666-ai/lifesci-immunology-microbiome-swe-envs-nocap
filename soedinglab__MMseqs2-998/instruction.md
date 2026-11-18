# Issue

**Title:** Introduce simd_any()/simd_eq_all(), optimize simd_hmax*() for Armv8 Neon

## Description

Most of manually vectorized operations in StripedSmithWaterman.cpp are elementwise, and in such cases there is a single instruction emitted for both SSE/AVX and Neon, providing maximum performance on all the platforms.
But there are few places where in SSE/AVX case we need few instructions, and some of them don't have direct Neon equialent.
As a result, on Arm platform we have a long chain of Neon instructions exactly replicating what SSE/AVX instructions do, but what algorithm actually needs can be implemented with just a single Neon instruction.
A good example is existing simd_hmax8_sse() which returns maximum across vector.
For SSE it has 5 instructions:
```
inline uint8_t simd_hmax8_sse(const __m128i buffer) {
    __m128i tmp1 = _mm_subs_epu8(_mm_set1_epi8((char)255), buffer);  // psubusb
    __m128i tmp2 = _mm_min_epu8(tmp1, _mm_srli_epi16(tmp1, 8));      // psrlw, pminub
    __m128i tmp3 = _mm_minpos_epu16(tmp2);                           // phminposuw
    return (int8_t)(255 -(int8_t) _mm_cvtsi128_si32(tmp3));          // movd
}
```
Performant Neon implementation is just a single instruction:
```
inline uint8_t simd_hmax8_sse(const __m128i buffer) {
    return vmaxvq_u8(vreinterpretq_u8_s64(buffer));                  // umaxv
}
```

Proposal is to introduce additional simd_any()/simd_eq_all() functions similar to existing simd_hmax*() functions, which cover those non-elementwise operations.
And then, for simd_any()/simd_eq_all()/simd_hmax*(), have separate SSE/AVX and Neon implementations providing best performance on each platform.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42f129b6bbea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.