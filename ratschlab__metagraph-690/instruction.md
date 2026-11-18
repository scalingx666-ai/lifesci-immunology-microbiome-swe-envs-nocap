# Issue

**Title:** Fix dangling references in the labeled aligner's annotation buffer

## Description

## Problem

`LabeledAligner` segfaults after many `align()` calls on one aligner object. A language binding drives the aligner this way. The batched CLI is not affected, because it builds a new aligner per batch.

Reproduction:
- 24 RefSeq bacterial genomes, k=31 CANONICAL graph, column annotation.
- 1000 simulated ONT reads (400 bp, 97% identity), full-k seeds.
- One `LabeledAligner`, `align()` called once per read.
- SIGSEGV on read 981. That read aligns fine when it runs alone or with only its 20 predecessors.

Root cause, found with an assertion-enabled build: `assert(val != nannot)` fails at the end of `AnnotationBuffer::fetch_queued_annotations`.

## Fixes

Two dangling-reference bugs, both in `AnnotationBuffer`, the aligner's per-object label cache:

1. **`fetch_queued_annotations`, CANONICAL graphs (the crash).**
   - A node whose canonical counterpart is already registered is inserted into `node_to_cols_` with `try_emplace`.
   - The code then reads the counterpart's value through the iterator `find_b`.
   - When the insert reallocates the vector-backed map, `find_b` dangles. The node can be left unqueued and keep the "not fetched" marker.
   - `LabeledAligner::filter_seeds` then dereferences a null label pointer; the guarding `assert` is compiled out in Release.
   - Fix: copy the value before inserting.
2. **Cached label sets.**
   - `LabeledExtender` holds references from `get_cached_column_set()` and `get_labels_and_coords()` while it caches new intersected label sets in the same loop.
   - The sets lived in a vector, so caching could move them.
   - Fix: store them in a deque (`VectorSet` with a `std::deque` container), so caching never moves existing sets.
   - The same issue was noticed earlier on `hm/align_nomutex` (414cfb06c), which re-fetched the reference per iteration; that commit never reached master.

## Tests

- `LabeledAlignerTest.CachedColumnSetsKeepTheirAddress`: references to a cached set and to a node's labels stay valid while 10,000 new sets are cached.
- `LabeledAlignerTest.FetchBothStrandsInOneBatch`: on a CANONICAL graph, queueing the forward and reverse-complement paths of a 5 kbp sequence in one batch fetches labels for every node.
- Locally, with an assertion-enabled `-O2` build: 14/14 test instances pass. The full suites were not run locally.
- Negative control: with the vector container restored, `CachedColumnSetsKeepTheirAddress` fails on 7/7 graph and annotation types.
- `FetchBothStrandsInOneBatch` exercises the iterator path, but it cannot catch that bug deterministically: the bug is a read after reallocation, which needs a sanitizer to detect reliably. The crash reproduction below is the evidence for that fix.

## Before / after (benchmark harness, branch `bench/align-harness`)

Setup:
- Driver: `align_bench`, one aligner reused across reads.
- 21 labeled arms: CANONICAL with full-k and seed-19 seeds, BASIC with seed 19.
- Reads: 150 bp Illumina-like, plus ONT 400 bp and 1–5 kb at 3/5/10% error.
- Before and after were interleaved, 4 single-threaded arms at a time.

| | before (`8b77fc8f9`) | after |
|---|---|---|
| reads crashing the process | 1 (`r980`, SIGSEGV) | 0 |
| arms with identical output (all columns but latency) | — | 20/21 |
| the remaining arm | `r980` CRASH | `r980` aligned to its true genome, score 826 |

- Latency is unchanged within run-to-run noise. Examples, p50/p99 ms before → after:
  - CANONICAL seed 19, 400 bp 3%: 7.7/21 → 7.7/19;
  - long reads 3%: 71.9/344 → 70.1/317;
  - BASIC seed 19, long reads 5%: 31.3/172 → 32.3/182.
- Peak RSS is unchanged (0.2–0.8 GB).

### Multi-threaded CLI

`metagraph align -p 8`, CANONICAL graph, 945 long ONT reads (3/5/10% error). Master `8b77fc8f9` vs this PR, 3 interleaved repeats each; median wall (per-repeat values), peak RSS.

| config | master | this PR | peak RSS |
|---|---|---|---|
| labeled, seed 19 | 53.6 s (53.6/49.2/63.8) | 50.1 s (50.1/47.3/58.4) | 0.95–0.96 GB both |
| labeled, full k | 29.2 s (29.2/25.2/36.5) | 28.9 s (28.9/27.4/32.0) | 0.82–0.90 vs 0.80–0.86 GB |
| unlabeled, seed 19 (control) | 44.6 s | 42.9 s | 0.67–0.69 vs 0.65–0.71 GB |

- Output checksums are identical across all 18 runs.
- No regression beyond run-to-run noise. The laptop was shared, which explains the slower third repeat on both sides.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b77fc8f9e16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.