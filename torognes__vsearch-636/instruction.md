# Issue

**Title:** Avoid std::exit() from a worker thread on malformed query input

## Description

## Problem

`sintax`, `usearch_global`/`search`, `search_exact`, and `uchime_ref` read the
query file **inside their worker threads** (`fastx_next()` / `fasta_next()`).
On malformed input the shared FASTA/FASTQ parser calls `fatal()` (`std::exit()`)
directly from a worker thread while sibling workers are still running — reading
shared state and writing to the output streams.

`std::exit()` flushes and closes those shared streams and runs static
destructors concurrently with the live workers, which is a data race: it can
corrupt libc state and crash, and it can drop the error message before it
reaches the `--log` file. Because it depends on thread timing it is intermittent
and platform-dependent (more likely to surface with clang/libc on some
platforms; often benign on glibc/Linux).

## Fix

Add a deferred-error channel to the fastx handle: a `defer_errors` flag, an
`error` flag and message buffer, and `fastx_set_deferred_error()`. When
`defer_errors` is enabled, a parse error records its message and makes
`fastx_next()` return `false` instead of calling `fatal()`.

The converted parser sites — `fastx_filter_header()`, every `fastq_fatal()`
site in `fastq_next()`, and the `fasta_next()` / `fasta_filter_sequence()`
fatals — defer **only when the flag is set**, so all other callers keep the
original immediate-`fatal()` behavior and messages unchanged.

The four affected commands enable the flag on their query handle (their worker
loops already stop when `fastx_next()` returns `false`) and report any recorded
error with `fatal()` from the **main thread, after the worker pool has joined** —
so teardown is single-threaded and races nothing.

## Testing

- Normal FASTA/FASTQ runs are unchanged for all four commands.
- Each malformed class — illegal header character, illegal and unprintable
  sequence characters, truncated record, `+`-line and sequence/quality-length
  mismatches — now produces a clean error message and a non-zero exit, with no
  crash, for every affected command.
- Concurrent-abort stress (a bad record mid-stream, default thread count, many
  repetitions per command) is clean: no crashes or hangs.
- A ThreadSanitizer build reports no data races across the affected commands,
  all error classes, and the normal paths.
- No regressions in the FASTA/FASTQ parsing tests.

## Notes

The behavior for valid input, and for the database / denovo code paths (which
read on the main thread), is unchanged. Commands that load the whole database on
the main thread (`cluster`, `allpairs`, masking) were already unaffected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bba838cb403`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.