# Issue

**Title:** Optimizations for annotations with dense matches

## Description

Significantly reduces query time and RAM usage for dense rows with many matches (e.g., COVID or Human graphs).

### Changes

  1. **Remove RowDiff row deduplication** (`row_diff.hpp`, `int_row_diff.hpp`, `tuple_row_diff.hpp`) — Replace `VectorSet` hash dedup with 1:1 mapping. Benchmarks showed dedup rarely shrinks batches much,   
  while its `#pragma omp critical` dominates query time. Also removes the batched `call_row` accumulator that was needed for thread safety under dedup.

  2. **Streaming row enumeration** (`annotated_dbg.cpp`) — `filter_and_aggregate` now takes a `RowEnumerator` callback instead of a materialized row vector. Fast paths for `UniqueRowBinmat` and `CSRMatrix`  
  stream rows via zero-copy accessors; other matrices fall back to batch fetch.

  3. **New `UniqueRowBinmat` capabilities** (`unique_row_binmat.cpp/hpp`) — Rebase from `RainbowMatrix` to `RowMajor`. Add `get_row_ref()` (zero-copy), `sum_rows()`, and a sort-based `get_rows_dict()`.      
  Remove unused `codes_to_rows()` and `num_distinct_rows()`.

  4. **New `CSRMatrix` accessors** (`csr_matrix.cpp/hpp`) — `get_row_values(Row)` returning `const&`, and `sum_rows()` for count aggregation.

  5. **`ValueStore` utility** (`algorithms.hpp`) — Hybrid dense/sparse store (dense vector for universe < 1M, `hopscotch_map` otherwise). Replaces `hopscotch_map<Column, ValueType>` in                       
  `filter_and_aggregate`.

  6. **Remove `call_annotated_nodes`** (`annotated_dbg.hpp/cpp`, `test_annotated_dbg.cpp`) — Deleted; sole test call site inlined to `get_annotator().call_objects()`.


### Benchmark
```
**COVID DNA index (row_diff_brwt)**
  metagraph_DNA query /data/scratch/covid.fa -p 30 -i .../SARS_Cov2/0017/graph.primary.small.dbg -a
  .../SARS_Cov2/0017/annotation.clean.row_diff_brwt.annodbg --batch-size 1000000000 --num-top-labels 500 --query-mode *

Mode      | Time (s)       Speedup | Annot query (s)  AQ speedup | RAM (GB)       | RAM overhead (GB)
labels    | 54.8 ->  20.7  2.6x    | 47.9 ->  13.5    3.5x       | 49.1 -> 27.3   | 44.7 -> 22.9
matches   | 54.0 ->  20.8  2.6x    | 47.1 ->  13.7    3.4x       | 49.1 -> 27.4   | 44.7 -> 23.0
signature | 88.3 ->  26.3  3.4x    | 81.4 ->  19.2    4.2x       | 71.4 -> 27.3   | 67.0 -> 22.9

**COVID RNA index (row_diff_int_brwt)**
  metagraph_DNA query /data/scratch/covid.fa -p 30 -i .../graph.primary.small.dbg -a
  .../annotation.clean.row_diff_int_brwt.annodbg --batch-size 1000000000 --num-top-labels 500 --query-mode *

Mode      | Time (s)       Speedup | Annot query (s)  AQ speedup | RAM (GB)       | RAM overhead (GB)
labels    | 27.7 ->  20.4  1.4x    | 17.9 ->  11.0    1.6x       | 21.6 -> 21.6   |  8.1 ->  8.1
matches   | 26.8 ->  20.4  1.3x    | 17.4 ->  11.1    1.6x       | 21.6 -> 21.6   |  8.1 ->  8.1
signature | 31.5 ->  21.6  1.5x    | 22.0 ->  12.3    1.8x       | 25.2 -> 21.6   | 11.7 ->  8.1
counts    | 41.2 ->  23.9  1.7x    | 30.7 ->  13.3    2.3x       | 43.6 -> 30.0   | 30.1 -> 16.5

**Bacteria index (row_diff_brwt)**
  metagraph_DNA query .../100_studies_5k_short.fq -p 30 -i .../superkingdom_bacteria/0052/graph.primary.small.dbg -a
  .../superkingdom_bacteria/0052/annotation.clean.row_diff_brwt.annodbg --batch-size 1000000000 --query-mode *

Mode      | Time (s)        Speedup | Annot query (s) AQ speedup | RAM (GB)       | RAM overhead (GB)
labels    | 118.7 -> 116.7  1.02x   |  7.4 ->  7.1    1.04x      | 10.0 -> 10.0   |  3.6 ->  3.6
matches   | 118.0 -> 118.9  0.99x   |  7.5 ->  7.2    1.04x      | 10.0 -> 10.0   |  3.6 ->  3.6
signature | 119.8 -> 121.9  0.98x   | 10.2 ->  9.5    1.07x      | 10.0 -> 10.0   |  3.6 ->  3.6
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e69e1282f551`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.