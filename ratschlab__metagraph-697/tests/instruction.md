# Issue

**Title:** Fix the seed coverage count and skip the redundant second strand on CANONICAL graphs

## Description

Replaces #695. Two commits:
1. Fix the count of query characters covered by seeds.
2. Skip the second strand on CANONICAL graphs when it is redundant, which recovers the speed the fixed count would otherwise cost.

## 1. Seed coverage count

**Bug.** `get_num_char_matches_in_seeds` stops counting at the first seed with a non-zero offset (a sub-k seed). Its skip loop compares the seed it started from instead of the current one, so it walks to the end. It also lowers the covered end after a contained seed. The count is now the size of the union of the seeds' query ranges. The test covers offset, overlapping, duplicate, contained, unsorted and empty seeds; the old code returns 5 instead of 15 on the first case.

**Where it mattered.**
- **Seed-chain check against `min_exact_match`.** Chaining is always on with a coordinate annotation, so on BASIC graphs with `column_coord` most reads with indels were rejected: ONT 400 bp at 3% error, 20% aligned against 93% with a plain annotation.
- **Strand choice in the labeled aligner** (`filter_seeds` → `rel_score_cutoff`). The undercount skipped one strand more or less at random.

## 2. Second strand on CANONICAL graphs

On CANONICAL graphs a query and its reverse complement match the same k-mers, so the corrected counts let the second strand through almost always. On 4515 reads that cost +35% wall time on CANONICAL labeled seed-19 alignment, for:
- 7 label-set changes;
- 3 higher scores;
- about 450 rows that changed only in CIGAR, i.e. mirror alignments.

The second strand is now skipped on CANONICAL graphs when the first strand already produced an alignment spanning ≥95% of the query. This includes PRIMARY, which is aligned through the canonical wrapper. The threshold is a fixed constant, not tied to `rel_score_cutoff`, which defaults to 0 in `DBGAlignerConfig`. There is no new option.

The gate is off on BASIC graphs and whenever alternative alignments are requested (`num_alternative_paths > 1`).

Tests:
- the rule itself: span threshold, BASIC, alternatives;
- both strands of a query on CANONICAL with the library-default config (`rel_score_cutoff` 0);
- CANONICAL with `num_alternative_paths = 3`: 3 alignments for a query and its reverse complement, the same count master returns.

## Expected output changes
- **CANONICAL / PRIMARY:** label sets, strands and scores change on a few reads; most changed rows differ only in CIGAR (mirror alignments).
  - Labeled seed 19: no read scores lower than on master.
  - Full-k labeled and unlabeled alignment (including `query --align` and the server on CANONICAL graphs) are now gated too. They are about 22% faster; 0–3 reads per 1000 score 0.1–2% lower; aligned fraction unchanged.
- **BASIC, plain annotation:** scores only go up (12–34 reads per set); top-1 improves.
- **BASIC, coordinate annotation:** many more reads align. Wall time grows accordingly (long reads 8.6 s → 19 s), because master was dropping them.
- **With `--align-alternative-alignments N`** (gate off): more reads reach N alternatives. Master skipped the second strand by accident. On ONT 400 bp, 3 requested: 427 reads go from 1 to 2. The extra ones are same-strand, same-label variants.
- **Unchanged:** protein graphs (no strand rule).

## Numbers
**Setup:** 24 RefSeq bacterial genomes (92 Mbp), k=31, 24 labels (plus a 192-label variant). Reads from `badread`. `min_exact_match` 0.7.

**Aligned fraction / top-label precision (master → PR):**

| reads | BASIC plain | BASIC coordinates | CANONICAL plain | PRIMARY plain |
|---|---|---|---|---|
| Illumina-like 150 bp (2100) | .952/.908 → .952/.922 | .883/.854 → .952/.922 | .952/.951 → .952/.951 | .952/.951 → .952/.951 |
| ONT 400 bp, 3% (1050) | .928/.882 → .928/.915 | .201/.200 → .928/.916 | .928/.925 → .928/.923 | .928/.925 → .928/.923 |
| ONT 400 bp, 5% (1050) | .665/.639 → .665/.658 | .050/.050 → .663/.658 | .667/.660 → .667/.663 | .665/.658 → .665/.661 |
| ONT 1–5 kb, 3% (315) | .946/.908 → .946/.946 | .003/.003 → .946/.946 | .946/.946 → .946/.946 | .946/.946 → .946/.946 |
| random 400 bp + 1–5 kb (600) | 0 → 0 | 0 → 0 | 0 → 0 | 0 → 0 |

**`align -p 8` wall time:** 945 long ONT reads, 3 interleaved repeats, median s. Peak RSS within ±5% except BASIC coordinates (0.81 → 0.97 GB).

| configuration | master | count fix only | this PR |
|---|---|---|---|
| CANONICAL labeled, seed 19 | 48.6 | 65.6 | 49.7 |
| PRIMARY labeled, seed 19 | 29.4 | 35.2 | 27.6 |
| CANONICAL, 192 labels, seed 19 | 92.8 | 114.0 | 89.3 |
| CANONICAL labeled, full k | 26.2 | 25.8 | 20.6 |
| CANONICAL unlabeled, seed 19 | 37.6 | 40.1 | 28.9 |
| BASIC labeled, seed 19 | 18.8 | 20.3 | 18.9 |
| BASIC coordinates | 8.6 | 19.0 | 19.1 |

**Per-read latency, single thread:** ms, p99 / max.

| reads | master | count fix only | this PR |
|---|---|---|---|
| CANONICAL, ONT long (945) | 327 / 1113 | 427 / 2184 | 296 / 879 |
| CANONICAL, ONT 400 bp 3% | 17.5 / 598 | 26.6 / 588 | 17.4 / 109 |
| PRIMARY, ONT long | 130 / 342 | 197 / 592 | 128 / 408 |
| CANONICAL 192 labels, ONT 400 bp 3% | 42 / 598 | 49 / 580 | 36 / 145 |
| CANONICAL low-complexity / tandem repeats (300) | 23.5 / 23.8 | 23.7 / 24.2 | 23.7 / 23.9 |

The "this PR" columns were measured with an experiment build that has the same rule. The PR binary's output is byte-identical to it on ONT 400 bp and ONT long reads for CANONICAL, PRIMARY and BASIC.

### Larger graph: 300 RefSeq complete genomes (1.22 Gbp), CANONICAL, k=31, one label per genome

Setup:
- 250 species, plus 5 extra strains for each of 10 well-sampled species.
- Graph 1.24 GB, annotation 1.7 GB.
- Reads simulated the same way as above, from these genomes.

**Accuracy** (aligned / top-1 identical in aligned fraction for every set; master → PR):
- Labeled, seed 19:
  - Illumina-like .952/.952 → .952/.952;
  - ONT 400 bp 3% .928/.927 → .928/.927;
  - ONT 400 bp 5% .681/.678 → .681/.680;
  - ONT long 3% .943/.940 → .943/.937 (1 of 315 reads).
  - No read scores lower than on master.
- Labeled, full k: identical outputs on every set.
- Unlabeled: 1–3 reads per set score lower; aligned fraction unchanged.
- Random reads accepted: 0/600 for both, in all three configurations.

**`align -p 8` wall time** (1050 ONT 400 bp + 315 ONT long reads, interleaved, median):

| configuration | master | this PR | peak RSS master / PR |
|---|---|---|---|
| labeled, seed 19 (8 repeats) | 83.6 s | 83.6 s | 3.80 / 3.83 GB |
| labeled, full k (3 repeats) | 74.4 s | 60.3 s | 3.69 / 3.74 GB |
| unlabeled, seed 19 (3 repeats) | 19.0 s | 14.1 s | 1.79 / 1.82 GB |

**Per-read latency, single thread, labeled seed 19** (1365 reads):
- master: total 107.2 s, p50 37 ms, p99 388 ms, max 722 ms;
- this PR: total 101.7 s, p50 33 ms, p99 376 ms, max 636 ms.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7a7b1207cce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.