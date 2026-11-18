# Issue

**Title:** Schedule AMG pair solves in equal-sized chunks rather than by source node

## Description

## The problem
`solve_pairs!` for CG+AMG spawned one task per **source node**. That has two effects:

1. **Triangular load** — task 1 solves n−1 pairs, task n solves none. Only bites when the number of focal nodes is small relative to threads (P < 2T); with P ≫ T the scheduler balances fine.
2. **The default configuration was serial.** With no maps requested (`write_cur_maps = False`, the default) the resistance shortcut anchors every pair at a single source — one group — so all P−1 solves ran in **one task**, whatever `-t` was.

## The change
Flatten the jobs and split them into equal-count chunks, ~4 per thread (`min(length(jobs), 4 * nthreads())`). Every pair costs about the same (same matrix, same preconditioner), so equal counts are equal work; a few chunks per thread leaves slack for stragglers while still amortizing the per-task preconditioner-workspace copy — fewer copies than before (P → ~4T). `handle_pair` was already safe for concurrent callers; nothing else changes.

## Measured (400×400 random-resistance grid, 8 threads unless noted, best of 3; rebased on master `30dce06`)
| case | before | after |
|---|---|---|
| shortcut (default), P=16 | 2.37 s | **0.64 s** |
| all pairs, P=16 (119 pairs) | 5.20 s | 4.66 s |
| all pairs, P=9 (35 pairs) | 1.97 s | 1.72 s |
| all pairs, P=80 (3,160 pairs), 4 threads | 19.6 s | 20.1 s (noise) |

## Measured at scale (2000×2000 random-resistance grid, 4M cells, 8 threads, machine otherwise idle)
| case | before | after |
|---|---|---|
| shortcut (default), P=16 (15 solves) | 73.9 s | **20.4 s** |
| all pairs, P=9 (35 solves), rep 1 / rep 2 | 59.6 s / 59.8 s | 48.2 s / 56.2 s |

The shortcut case is the one that matters for typical use — no maps requested — and it is where the old per-source split left every solve on a single task. The all-pairs gain is modest and noisy at this size (memory-bandwidth bound); a first AFTER reading of 78 s was taken while other Julia jobs were running and did not reproduce.

Full suite: Unit 60/60; CG+AMG/CHOLMOD × Float64/Float32 all 719/719; Issue 341 46/46.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `30dce06de4de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.