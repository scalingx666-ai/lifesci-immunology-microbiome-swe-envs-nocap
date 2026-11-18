# Issue

**Title:** arda 2.9.0 — --indel-rescue: an ungapped extension cannot score a read that has an indel

## Description

## What

`--indel-rescue` (off by default, `--fast-segments` only). An ungapped extension follows **one** diagonal, so a read carrying an indel relative to germline scores only up to the indel. The unit test measures it: a 120 nt read scores **240** clean and **120** — exactly half — with a single base deleted. Its scaffold is then chosen on truncated evidence.

## Why it matters

Measured on **341,294 real IGH mates** (two IGH RepSeq amplicons, IgBLAST truth, read straight off the gapped alignment strings — no cigar, nothing inferred):

| V identity | `>=98` | `95-98` | `90-95` | `<90` |
|---|---|---|---|---|
| reads carrying a V indel | 0.74 % | 1.63 % | 3.56 % | **8.00 %** |

3.18 % pooled, tracking SHM load because AID makes indels and not only substitutions.

## Rerouted, never dropped

A flagged read is demoted from `implied` to `rescue` and realigned **gapped**, after `shortlist()` has asserted its partition is total. A false positive costs a little speed and cannot cost a read — that asymmetry is why the support threshold is deliberately low. Counted as `indel_rescued` in the report.

## ⚠ Recall cannot measure this flag

Recall is identical with and without it (174,066 of 174,226 amplicon fragments either way): these reads are found regardless. What moves is the **call**, which is load-bearing because the clonotype key is `(locus, v_call, j_call, junction)` at allele level. Adjudicated against IgBLAST at gene level on exactly the reads whose call moved:

| sample | v_call moved | correct without | correct with |
|---|---|---|---|
| IGH_repertoire (hypermutated) | 586 | 53.24 % | **84.13 %** |
| IGH_naive (low SHM) | 100 | **77.00 %** | 63.00 % |
| **pooled** | **686** | 56.71 % | **81.05 %** |

**+167 reads, +24.3 points.** The sign flip is the mechanism confirming itself: where real indels are common the flag fixes truncated calls; where they are rare its false positives (repeats read as two diagonals) dominate.

On 13 bulk RNA-seq datasets it demotes **zero** reads and the output is byte-identical — correct, since bulk TR carries ~0 indels.

## Also recorded

`--fast-segments` is **1.87× at 41 % less RSS** on real IGH amplicon, and ⛔ every `fast_fraction` figure in the `--two-pass` docs is **MMseqs2-specific**: 0.052 with the mmseqs segment search vs **0.5018** with `--fast-segments` on the same reads.

## Verification

539 tests pass (10 new), `ruff check src/` clean, docs build with `-W`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c01df7d4335d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.