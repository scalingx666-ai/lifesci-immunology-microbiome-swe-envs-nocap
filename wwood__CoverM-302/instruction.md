# Issue

**Title:** fix strobealign log error

## Description

Summary

Fix a panic in complete_processes that hides the real mapping error when a mapper's captured stderr log can't be decoded as UTF-8, and add regression tests.

Background

A downstream project (binchicken) hit CoverM failures when mapping with strobealign 0.17.0 against .fastq.gz reads on certain filesystems/sandboxes. Two related failures were reported:

thread 'main' (10381) panicked at src/bam_generator.rs:266:37:
Failed to read log file for STROBEALIGN
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace

[2026-07-10T01:11:32Z ERROR coverm::bam_generator] The STDERR for the STROBEALIGN part was: This is strobealign 0.17.0
    strobealign: mmap failed to open file: /tmp/tmpxu7laryn/test/coassemble/qc/SRR8334323_1.fastq.gz: Invalid argument

[2026-07-10T01:11:32Z ERROR coverm::bam_generator] Cannot continue since mapping failed.

The second log shows the actual underlying cause (strobealign itself fails to mmap the input FASTQ, an upstream/environment issue — --mapper minimap2-sr works around it). The first log is a separate, genuine CoverM bug: complete_processes read the captured mapper stderr with read_to_string, which errors out on non-UTF-8 bytes (e.g. progress/control characters some mappers write to stderr). That error was turned into a panic via unwrap_or_else(|_| panic!(...)), which crashes CoverM outright and destroys the real error message before the user ever sees it — as happened in the first log above.

Changes

- Extracted the log-reporting loop in complete_processes into report_log_contents.
- Read the log as raw bytes (read_to_end) and decode with String::from_utf8_lossy instead of read_to_string, so non-UTF-8 stderr no longer causes a decode error.
- On a genuine I/O error (rather than a decode error), log a warn! and continue instead of panicking, so one unreadable log doesn't take down the whole run or hide the actual mapping failure.
- Added two unit tests in bam_generator::tests:
  - test_report_log_contents_does_not_panic_on_invalid_utf8 — reproduces the exact panic from the first log above. Fails against the old code, passes with the fix.
  - test_report_log_contents_does_not_panic_on_valid_utf8 — uses the actual "mmap failed to open file... Invalid argument" text from the second log as a baseline check.

Scope / non-goals

This does not fix strobealign's mmap failure itself — that lives in the external strobealign binary (or the filesystem it's running on) and is outside CoverM's control. This PR only ensures CoverM surfaces the real error instead of panicking and hiding it.

Test plan

- [x] cargo build --tests compiles cleanly, no new warnings
- [x] cargo test bam_generator::tests — both new tests pass
- [x] Verified regression coverage: temporarily reverted report_log_contents to the old logic, confirmed the invalid-UTF-8 test fails with the same panic message/location as the original bug report, then restored the fix and confirmed both tests pass again

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e5e6c780ec4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.