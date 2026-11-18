# Issue

**Title:** perf: reduce groot indexing overhead

## Description

Reduce a handful of overheads in the indexing path:

- flatten the pipeline stage handoffs in `src/pipeline/index.go`
- reduce merge-key allocation churn in `src/graph/graph.go`
- preallocate per-window contained-node maps
- keep the earlier MinHash/seqio cleanup in place

Validation:
- `go test ./...`
- `BenchmarkIndexing` improved from about 680.5 ms/op to about 643.4 ms/op in local runs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1be76fa31d98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.