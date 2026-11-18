# Issue

**Title:** Buffer --output-file writes

## Description

.

`OutputWriter` wrapped a bare `std::fs::File`, so each small `write!()` became its own `write()` syscall, about one per byte. Writing a 1.49M-contig × 399-sample `metabat` matrix (2.5 GB) with `--output-file` took ~66 min on Lustre, about as long as reading the 436 GB of BAMs. Details are in #306.

Changes, all in `src/lib.rs`:
- Wrap the output file in a `std::io::BufWriter`.
- Add a `Drop` for `OutputWriter` that flushes explicitly and logs an error if the final write fails. `BufWriter`'s own drop-time flush ignores errors, so without this a failed write would silently truncate the output.
- The stdout path is unchanged; it is already line-buffered.

The output from the buffered path should be identical. Piping stdout (`| cat > file`) as a workaround gave byte-identical results to `--output-file` on a 100,967-contig × 17-sample run.

Testing: I could not build locally (no Rust toolchain on hand), so this relies on CI's `cargo test`. The change is confined to `OutputWriter`, and only `src/lib.rs` constructs it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04190753539b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.