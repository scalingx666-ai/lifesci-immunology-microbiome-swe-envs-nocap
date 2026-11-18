# Issue

**Title:** 2.18.1 — the coverage assignment's inner scan, bounded in C++

## Description

`_assign_coverage` is 80 % of `correct` (2.20 s of 2.74 s on a 100 k TRA amplicon). Its inner scan compared an integer mismatch count against a FLOAT budget one base at a time in Python, over a measured **3.55 M candidate diagonals per 20,000 reads**.

⛔ Unlike the assembler's overlap test in 2.18.0, this caller needs the **count**, not a verdict: a read joins the root with the longest overlap and, **on a tie, the fewer mismatches**. That tie-break is load-bearing — ~47 % of the 5,758 reads the Jurkat phantom clonotype stole were exact 48-vs-48 overlap ties where the losing TRUE root matched with 0 mismatches against the phantom's 1.

`_markup.count_mismatches` returns the **true count** whenever the row is accepted and collapses to `max_mm + 1` only when the row is rejected anyway, so both the accept test and the tie-break see exactly what they saw before. Equivalence: for an integer count, `mm > budget` is exactly `mm > floor(budget)`.

| | before | after |
|---|---|---|
| `correct`, TRA amplicon 100 k | 3.23 s | **2.84 s** (1.14×) |
| `correct`, bulk RNA-seq 660 k pairs | 1.10 s | **0.95 s** (1.16×) |

`clones.tsv` **byte-identical on both regimes**. A patch release: no output, flag or default moves.

## Tests

850 across three tiers. The parametrised test checks accept, reject AND the returned count against the Python it replaces across 30 budget/sequence combinations; three plausible wrong implementations (ceil instead of floor, returning a bool, an off-by-one early exit) each disagree on 7–12 of 15 spot cases.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e8889537a12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.