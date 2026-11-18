# Issue

**Title:** Expose profiling/sketching internals as a public library API

## Description

## Summary

Python bindings ([pysylph](https://github.com/althonos/pysylph)) currently keep private copies of sylph's profiling and sketching code, because those functions are private. This PR makes them `pub` so pysylph (and other Rust users) can call sylph directly and pick up fixes and new releases without re-copying code. It only changes visibility and adds one constructor, so the CLI behaves exactly as before.

```diff
 src/contain.rs
-fn get_stats / finalize_stats / compute_dense_survivors / minimum_ani_fraction
-fn winner_table / derep_if_reassign_threshold / estimate_true_cov
-fn estimate_covered_bases / bootstrap_interval / ani_from_lambda / get_kmer_identity
-struct Finalized { .. }
+pub fn ... (same functions)
+pub struct Finalized { pub .. }

 src/sketch.rs
-pub(crate) type Marker
-fn pair_kmer / pair_kmer_single / dup_removal_lsh_full / dup_removal_lsh_full_exact
+pub type Marker
+pub fn ... (same functions)

 src/cmdline.rs
+impl ContainArgs {
+    /// All fields at their CLI defaults; pseudotax = true for `profile`, false for `query`.
+    pub fn from_cli_defaults(pseudotax: bool) -> Self   // parsed via clap, stays in sync with the CLI
+}
```

`from_cli_defaults` saves library users from writing out all ~50 `ContainArgs` fields by hand. Today every new CLI option breaks downstream builds; with this constructor it doesn't.

**Second commit: Zero-copy in-memory two-stage databases:** Sylph no longer copies a .syl2db database when opening it from memory, and no longer copies every genome when converting a database. This roughly halves memory use for library users such as pysylph.

## Notes

- `cargo test`: all existing tests pass (25 unit, 2 main, 17 integration).
- 3 new tests check that `from_cli_defaults` matches `sylph profile` / `sylph query` argument parsing (for example `min_number_kmers = 10`, `min_contain = 7`, and the mode-dependent minimum ANI of 0.95 / 0.90).
- I ported pysylph to this branch. Its vendored copies of these functions were removed, and its profile/query results match the sylph v1.0.0 CLI on `test_files` (e.g. o157 vs E. coli DB: ANI 99.79 / 98.32 / 98.22 in both).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f7fcb53aa20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.