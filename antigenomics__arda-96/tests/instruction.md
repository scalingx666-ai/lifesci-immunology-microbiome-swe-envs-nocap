# Issue

**Title:** arda 2.11.1 — reuse the junction anchor prefix

## Description

`_anchored_vj_bounds` already computes the longest prefix of the junction that the called V's
germline templates. `v_anchor_prefix` then recomputed **the same scan over the same slice** to feed
the Cys104 junction gate — `_junction_nt` cuts `query_seq[cs-3-1 : f4+2]`, byte-identical to the
window `_anchored_vj_bounds` builds. It now returns that number and the gate reuses it.

| workload | 2.11.0 | 2.11.1 |
|---|---|---|
| TRA amplicon 100 k, 8 threads | 5.55 s | **5.35 s** |
| bulk RNA-seq 100 k, 8 threads | 2.60 s | **2.51 s** |

Output is **byte-identical** on both an amplicon and a bulk library. 624 tests pass.

Cumulative over this session's four earlier ports plus this one, same workload: **5.96 s → 5.35 s
(10.2 %)** against MiXCR's 5.90 s — 1.10× faster on wall, **12.7 s of CPU against 45.2 s**, and
631 MB against 3,027 MB.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7f9a8edbf3c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.