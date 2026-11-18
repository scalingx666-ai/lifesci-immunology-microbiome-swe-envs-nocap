# Issue

**Title:** Saturate k-mer match counter to avoid wraparound dropping hits

## Description

The per-target shared-k-mer counter (count_t, an unsigned short) was incremented with a plain ++ on the sparse-list path in search_topscores (searchcore.cc). A query that shares more than 65535 distinct k-mers with one target wraps that counter back toward 0; the wrapped value can then fall below minwordmatches and the true best target is silently dropped from the candidate set (or mis-ranked in the minheap).

The SIMD bitmap path (increment_counters_from_bitmap*) already increments these counters with signed saturation and so caps at INT16_MAX (32767). Both paths update the same counter array, so leaving the scalar path to run past 32767 is also internally inconsistent: a value the scalar path pushes into 32768..65535 is negative when the SIMD path reinterprets the counter as signed, and a subsequent saturating increment there can drive it back through zero.

Saturate the scalar increment at INT16_MAX to match the SIMD path. This keeps every counter in [0, 32767], where the two paths agree and neither can wrap; the cap is far above any realistic minwordmatches, so a high-overlap target stays a top candidate. Values below the cap (all ordinary data) are unaffected.


Claude-Session: https://claude.ai/code/session_01H6v7rX4pGLAL5BT2EWWxMM

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fad6841a49c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.