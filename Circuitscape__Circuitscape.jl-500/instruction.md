# Issue

**Title:** Skip postprocessing when no map output is requested

## Description

Part of the unreleased 6.0. Found while profiling for the architecture review.

## The problem
`postprocess` gated only the *file writes* on the output flags. With no maps requested — the common configuration — every pair still ran `write_cur_maps` → `_create_current_maps` → `get_node_currents`: two sparse branch-current matrices, a sparse transpose and subtraction, `dropzeros!`, a full-grid scatter into a fresh `zeros(nrows, ncols)`, and a locked accumulate into a cumulative map nobody would read. Profiling a 1M-cell, 629-pair CG+AMG run with no maps on 8 threads: **19% of samples** (26k of 137k) were in this path, and the run allocated **670 GiB — about 1 GB per pair** — almost all of it here.

## The change
After the shortcut branch, `postprocess` returns unless `write_volt_maps`, `write_cur_maps`, `write_cum_cur_map_only` or `write_max_cur_maps` is set. One consequence worth stating: **network mode** used to write per-pair `*_node_currents_i_j.txt` / `*_branch_currents_i_j.txt` files regardless of `write_cur_maps` (the guard was commented out); it now honours the flag exactly as the raster path does. The cumulative network files were already gated on it.

## Measured (400×400 grid, P=16, 119 pairs, shortcut defeated, no maps, 8 threads; taken while other test suites were running on the machine)
| | time (best of 3) | allocated per run |
|---|---|---|
| master | 4.96 s | 20.28 GiB |
| this PR | **3.31 s** | **3.49 GiB** |

The 1M-cell figure above is the real-world weight; the small case is for reproducibility.

## Tests
New test in `internal.jl`: raster run with maps off produces no map files and identical resistances to the maps-on run; network run with `write_cur_maps = False` produces no per-pair current files. Full suite: Unit 501/501, CG+AMG and CHOLMOD × Float64/Float32 685/685 (fast path), Issue 341 46/46.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee086ec52def`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.