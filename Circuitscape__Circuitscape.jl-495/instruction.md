# Issue

**Title:** Replace Graphs with connected components computed on the CSC structure

## Description

## Why
Graphs was used for exactly one call — `connected_components(SimpleGraph(A))` — at six sites. Constructing the `SimpleGraph` first copies the adjacency structure into per-vertex lists. Measured on a 2000×2000 eight-neighbour grid (4M nodes, 32M nonzeros):

| | time | allocated | retained |
|---|---|---|---|
| `SimpleGraph(A)` + `connected_components` (Graphs) | 0.73 s | **1,574 MB** | 458 MB |
| `connected_components(A)` (this PR) | **0.32 s** | 140 MB | 0 |

That 1.5 GB was allocated once per run, on the critical path before any solve, on exactly the runs where memory is the complaint (#232, #292, #415). `using Circuitscape` also drops 2.71 → 2.28 s.

## What
`connected_components(A::SparseMatrixCSC)` in `utils.jl` walks `rowvals`/`nzrange` directly with a label vector and an explicit stack (iterative — a 4M-vertex component would overflow a recursive DFS). It keeps Graphs' contract exactly, verified against its source: nonzero *stored* entries are edges (stored zeros are not), the diagonal is ignored, components are ordered by their smallest vertex, vertices ascend within each. That ordering drives component iteration, `pair_numbers` in the log and the `comps` array, so every gold file stays byte-identical. Returns `Vector{Vector{Ti}}` in the matrix's index type rather than Graphs' fixed `Int`.

Six call sites lose the `SimpleGraph(...)` wrapper. Graphs, ArnoldiMethod, DataStructures, Inflate, SimpleTraits and Statistics leave the package.

## Tests
Graphs stays a **test-only** dependency for an equivalence test: identical output to `Graphs.connected_components(SimpleGraph(A))` on grid Laplacians (connected and with an isolated vertex), 200 random symmetric sparse graphs (many components, isolated vertices) in both `Int64` and `Int32` index types, and a matrix with explicitly stored zeros. Full suite: Unit 612/612, CG+AMG and CHOLMOD × Float64/Float32 all 719/719, Issue 341 46/46.

Independent of #493 (different files).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b5bb55c5201`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.