# Issue

**Title:** multi-graph server: support hosting multiple graphs in one process

## Description

* Support hosting multiple graphs
* Filter which ones to query with field `graphs` in the request json
* All query requests in the multi-graph mode share the same thread pool for querying individual graphs.

Usage:
`./metagraph server_query indexes.txt --mmap --parallel 50`

where indexes.txt is a csv file with graph names and paths:
```
human,human_chunk1.dbg,human_chunk1.row_diff_flat.annodbg
human,human_chunk2.dbg,human_chunk2.row_diff_flat.annodbg
microbe,microbe.dbg,microbe.row_diff_flat.annodbg
...
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `414e9259b272`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.