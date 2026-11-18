# Issue

**Title:** 2.18.0 — the assembler stops counting once the answer is known

## Description

## `assemble` is 4.49× faster, byte-identical

`_greedy_contigs`' overlap test asked `sum(1 for x, y in zip(a, b) if x != y) > (1 - min_id) * ov` — it counted **every** mismatch across the overlap and only then compared the total against the budget. Nearly every candidate it tests is a read that merely shares one k-mer and does not overlap at all, so the answer is settled in the first few bases and everything after it is dead work.

Profiled on a 100 k-read TRA amplicon: **153 million generator iterations, 19.5 s of the stage's 25.6 s.**

`_markup.within_mismatches(a, b, max_mm)` stops at `max_mm + 1`.

| | assemble | end-to-end |
|---|---|---|
| TRA amplicon, 100 k reads | 15.77 s → **3.52 s** (4.49×) | 27.00 s → **12.86 s** (2.10×) |
| bulk RNA-seq, 660 k pairs | 5.05 s → **3.53 s** (1.43×) | 23.14 s → **20.32 s** (1.14×) |

## Why the candidate set cannot move

The caller never used the count, only `count > budget`, and for an integer count that is exactly `count > floor(budget)` however the float lands. `clones.tsv` and `airr.tsv` are **byte-identical on both regimes** — the requirement, not a hope, since the contig sequence feeds every junction derived from it. Same 12 contigs / 19,841 clonotypes on the amplicon; same 1,931 contigs / 2,213 clonotypes on bulk.

The parametrised test checks the new predicate against the old `sum(...)` spelled out. Three plausible wrong implementations each disagree on 3–9 of its 14 cases (strict `<`; padding to the longer string; an off-by-one budget), so the test discriminates rather than merely passing.

## How it was found

By benchmarking the **full pipeline** instead of a stage. `arda amplicon` ran at 151 % CPU while `map` alone is multithreaded — which pointed at a single-threaded stage downstream of it.

## Not changed

`--assemble` stays the default in both modes. On the amplicon it costs what is now 27 % of the wall to rescue 12 reads of 43,503; on bulk it rescues 2,584 of 8,484. That asymmetry is read length against CDR3 length, not amplicon-vs-bulk — a 2×150 IGH amplicon with long CDR3s is the case the stage exists for, and it is not measured here.

## Tests

816 passed across all three tiers (unit + synthetic + realworld).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c22e97b6cd69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.