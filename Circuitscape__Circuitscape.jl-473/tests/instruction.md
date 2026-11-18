# Issue

**Title:** Honour included pairs in one-to-all/all-to-one and network modes

## Description

Stacked on #472 — that PR fixes the raster pairwise count, this one closes the two remaining places where the include/exclude pairs file is not applied correctly. Together they make #341 complete.

Review #472 first; this PR's base is that branch.

## 1. One-to-all / all-to-one: silently wrong resistances

`onetoall_kernel` indexes the include matrix with `i`, a position among the focal points **present in the point raster**, but the matrix rows are positions in `point_ids`, which comes from **the include file**. Those coincide only when every ID named in the file also exists in the raster. Otherwise every row after the missing one is shifted and the wrong nodes get grounded.

Point raster contains `{2,3,4}`; include file names `(1,2)` and `(3,4)`, where `1` is absent:

| node | before | after | expected |
|---|---|---|---|
| 2 | `-1` | `-1` | `-1` — its only listed partner (1) is absent |
| 3 | **1.90152** | 2.13636 | 2.13636 — the 3–4 resistance |
| 4 | 2.13636 | 2.13636 | 2.13636 |

`1.90152` is the **2–3** resistance: node 3 was grounded at node 2, which isn't a listed partner of 3 and was itself excluded from everything. Traced through the indexing: for node 3, `i=2` selected `include_pairs[2,:]`, which is ID 2's row.

Fix: look the row up by node ID (`findfirst(isequal(n), point_ids)`) rather than reusing `i`. The aligned case is unchanged — the control run (include file naming only existing IDs) returns identical values before and after.

Also drops a dead `points_unique = included_pairs.point_ids` that is overwritten a few lines later and made the indexing look correct.

## 2. Network mode: file ignored entirely

`get_network_data` never read `use_included_pairs`, and `network/pairwise.jl` hard-coded `exclude_pairs = Tuple{V,V}[]`. The file was silently discarded — the literal complaint in this issue's title.

Path graph `1-2-3-4`, include file naming only `(1,2)`:

| | before | after |
|---|---|---|
| `Total number of pair solves` | 6 | 1 |
| result matrix | 5×5, all pairs | 3×3, nodes 1 and 2 |

Fix: read it in `get_network_data`, carry it on `NetworkData`, apply it in `compute_graph_data`, pruning focal points not named in include mode exactly as the raster path does.

`docs/src/options.md` already says the feature affects all modes except advanced; that is now true rather than aspirational.

## 3. Shared helper, and one log-gating leftover

The mode-dependent half of `generate_exclude_pairs` is factored into `exclude_pairs_from`, which has no raster dependency, so raster and network share one implementation. Behavior is unchanged — the raster path still prunes first, then calls it.

The direct solver (`CHOLMOD`/`Pardiso`/`Accelerate`) still emitted the resistance-shortcut log lines ungated while the AMG solver's were gated in #472, and the pair-count line right beside them already was. Gated for consistency.

## Tests

Three new cases in `test/issue341.jl`: the one-to-all misalignment above, the network include file, and unit coverage of `exclude_pairs_from` in both modes.

Full suite, `JULIA_NUM_THREADS=4`: Unit 17/17, CG+AMG 719/719, CHOLMOD 719/719, Issue 341 **42/42** (28 on #472, 24 before it).

## Coverage after this

| mode | status |
|---|---|
| raster pairwise, single-cell nodes | fixed in #449 |
| raster pairwise, multi-cell regions | count fixed in #472 |
| raster one-to-all / all-to-one | fixed here |
| network pairwise | fixed here |
| advanced | N/A — documented as not applicable |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1db4a992116`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.