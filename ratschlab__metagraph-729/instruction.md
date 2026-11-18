# Issue

**Title:** Move brwt and row_diff_brwt annotations to an equal-k-mer graph with transform_anno --remap-graph

## Description

Existing annotations can now move to another graph with the same k-mers without annotating it again. The motivating case is serving the UHGG and gnomAD indexes with SSHash graphs. Re-annotating them would need the original genome files, could take days, and would not reproduce the relaxed and relabeled production annotation.

`metagraph transform_anno --remap-graph old.dbg -i new.sshashdbg -o out anno.row_diff_brwt.annodbg` matches rows by k-mer. It keeps the BRWT tree, the column order and every relation. Dropped rows, such as succinct dummy nodes, lose nothing because they hold no k-mer. For `row_diff_brwt`, each row keeps its successor from the old graph. The command writes those successors as the new successor bitmap, so query results are identical. The command stops if the graphs differ in any k-mer or if a non-anchor row would lose its successor.

Both graphs must be in basic mode. The row map is saved as `out.rowmap`. A rerun with the same output name reuses it and skips matching the rows again. Before reusing it, the command checks the row counts and 10,000 sample rows against both graphs.

With `--anno-type row_diff_flat` or `row_diff_disk`, a remapped `row_diff_brwt` annotation is converted in the same run, after the row map and the old graph are freed. Any other `--anno-type` is rejected.

I tested the same remap code on gnomAD, built on the older SSHash version that made its graph. The source had 29.0 B rows and the SSHash graph had 23.1 B nodes. The remap took 2 h 45 min on 32 threads with a peak RSS of 172 GB, of which about 2 h was the row map. `--query-mode labels` output for 5,747 contigs was identical before and after.

The full UHGG annotation (33.0 B nodes, 287 k labels) took 1 h 42 min on 64 threads with a peak RSS of 249 GB. Query output on two disjoint samples of about 5,100 contigs each was identical before and after.

I used Claude Code to write this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b14dfdb5949`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.