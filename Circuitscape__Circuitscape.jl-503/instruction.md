# Issue

**Title:** Replace linear scans in the pairwise driver with binary search

## Description

Part of the unreleased 6.0.

## The problem

Enumerating the pairs to solve cost O(pairs × n) before any linear algebra ran:

- `pair_jobs` did `findfirst(isequal(node), comp)` for both ends of every pair — `comp` is the component's node list, up to millions long — and `findall(isequal(node), points)` twice per pair.
- `solve` filtered `points` with `x in comp` per component and called `smash_repeats!` with another `findall` over `points`.
- `get_num_pairs` / `get_num_pairs_shortcut` did the same `x in cc` filter per component.
- In shortcut mode, `update_voltmatrix!` did `findfirst(isequal(point), cc)` for every point, for every pair solved, and `update_shortcut_resistances!` did `x in comp` per point.

At 300 focal points on a 1M-node component (~45k pairs) that is ~9 s of scanning to produce a job list — more than the solves themselves for a direct solver.

## The change

Components from `connected_components` list their nodes in ascending order (a documented contract of that function, and the only producer of `prob.cc`), so a node's local index and its membership are `searchsortedfirst` lookups: O(log n) per query, allocation-free. This is preferred over a per-component `Dict`/`Set`: hashing 1M node ids costs O(n) time and tens of MB per component for lookups we only need at ≤ a few hundred focal nodes, while binary search needs nothing built. `pair_jobs` checks `issorted(comp)` once (an O(n) pass over an already-materialized vector, negligible next to the existing per-component work) rather than assuming the contract.

- `component_index(comp, node)` / `in_component(comp, node)`: binary-search local index and membership.
- `component_points(comp, points)`: the `filter(x -> x in comp, points) |> unique` replacement, used by `solve`, `get_num_pairs` and `get_num_pairs_shortcut`.
- `point_positions(points)`: a `Dict{V,Vector{Int}}` from node id to the positions in `points` that map to it, built once per `solve` and passed to `pair_jobs` via a keyword (defaulting to building it, so the signature is otherwise unchanged). Replaces every `findall(isequal(node), points)`.
- `pair_jobs` also converts `exclude` to a `Set` once instead of scanning the vector per index combination.

The job list is identical in order and content (asserted against the old implementation in the benchmark below), so the log numbering and gold resistance files are unchanged. The solver-specific `solve_pairs!` methods are untouched.

## Measurements

Synthetic component of 1,000,000 sorted node ids, 300 distinct focal points (44,850 pairs), no exclusions. Best of 3, taken while other test suites were running on the machine, so treat wall-clock as indicative; `@allocated` is exact.

| step | old best-of-3 | old `@allocated` | new best-of-3 | new `@allocated` |
|---|---|---|---|---|
| `csub` filter (`component_points`) | 48.8 ms | 21.6 KiB | 18.0 µs | 21.6 KiB |
| `pair_jobs`, all pairs | 9.29 s | 15.3 MiB | 2.89 ms | 7.04 MiB |
| `pair_jobs`, shortcut (first source only) | 46.6 ms | 93.8 KiB | 314 µs | 38.1 KiB |

The remaining 7 MiB is the job list itself (44,850 `PairJob`s); the halving comes from sharing one positions vector per node instead of a fresh `findall` result per job (consumers only read them).

## Tests

- Full suite green with `JULIA_NUM_THREADS=4`: Unit tests 519/519, CG+AMG parallel Float64/Float32 685/685 each, CHOLMOD parallel Float64/Float32 685/685 each, Issue 341 46/46 (GeoTIFF fixtures skipped without ArchGDAL, as expected).
- New `pair_jobs` testset in `test/internal.jl`: a hand-derived synthetic case with two user points sharing one node, an excluded pair, a component node with no focal point, and a focal point outside the component; asserts the exact `(src_node, dst_node, comp_i, comp_j, src_indices, dst_indices)` list for the full and shortcut modes, the keep-if-any-combination-survives and drop-if-all-excluded rules, `component_index` against `findfirst` on `Int32`, the missing-node error, and the sorted-contract `ArgumentError`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62187e8845e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.