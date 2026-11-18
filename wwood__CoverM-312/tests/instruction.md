# Issue

**Title:** Pin hts-sys to 2.2.0 to fix build failures from binding drift

## Description

rust-htslib 0.46.0's hts-sys dependency range is loose enough that cargo can resolve a newer hts-sys release whose prebuilt bindings (e.g. core.isize renamed to
  core.isize_) no longer match rust-htslib's hand-written source, breaking `cargo install coverm` (#311). Pins hts-sys to the 2.2.0 release that rust-htslib 0.46.0 was actually
  built against.

  Tested with `pixi run cargo test` (142 passed, 0 failed, 4 ignored).

Closes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `730da9ccaf00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.