# Issue

**Title:** SSHash: RowDiffChar annotation format with sparse successor storage

## Description

## Summary

Add a new `RowDiffChar<BRWT>` annotation format (`.row_diff_char_brwt.annodbg`) optimized for SSHash graphs.

### Problem

The standard `row_diff_brwt` annotation stores a `fork_succ` bitvector (1 bit per node) to determine row-diff successors. For SSHash graphs with 67B+ nodes, this is ~8 GB. During query, finding the successor requires `adjacent_outgoing_nodes()` which enumerates all neighbors — expensive for SSHash where each neighbor lookup requires an MPHF hash.

### Solution

Exploit SSHash's `succ_is_next_` / `pred_is_prev_` bitvectors: ~94% of nodes have a trivially determinable successor (just `node ± 1`). Only the remaining ~6% non-trivial nodes need a stored 2-bit character.

**New data structures:**
- `rd_succ_needs_char_`: sparse bitvector marking which nodes need stored characters
- `rd_succ_char_`: compact `int_vector<2>` with 2-bit character indices for non-trivial nodes only

**Result on 67.3B-node graph:**
- Annotation size: 23 GB (vs 21 GB for standard rowdiff — the sparse char adds ~2 GB but removes the fork_succ bitvector)
- Query speed (2500 queries, nommap): RD step **32% faster**, BRWT step **19% faster**

### Key Changes

1. **`DeBruijnGraph::trivial_outgoing()`** — new virtual method returning the unique successor if resolvable in O(1). Default returns `npos`; only `DBGSSHash` overrides it.

2. **`DBGSSHash::traverse()` fast path** — checks `succ_is_next_` before falling back to MPHF lookup.

3. **`RowDiffMode::CharSucc` + `RowDiffChar<BaseMatrix>`** — new row-diff variant using sparse storage. Serialization format v3.0; v2.0 (Standard) completely unchanged.

4. **Transform path** — `row_diff_brwt` → `row_diff_char_brwt` via `compute_rd_succ_char()`.

### Backward Compatibility

- Succinct (DBGSuccinct) graphs use `RowDiffMode::Standard` (v2.0 format) as before — no code paths changed.
- `trivial_outgoing()` returns `npos` by default, so CharSucc mode is only activated when explicitly loading a v3.0 annotation with an SSHash graph.
- Old annotations load and work identically.

### Testing

- All 21 RowDiff unit tests pass
- All 476 annotation/BRWT/SSHash tests pass
- Query output verified identical (sorted diff) across rdchar and rowdiff for 1, 100, and 2500 queries

### Note on PR target

This PR targets `mk/brwt` (not `master`) since `mmap-sshash` is based on that branch. It should be reviewed/merged after or together with the mk/brwt → master PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `17ef279c1abd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.