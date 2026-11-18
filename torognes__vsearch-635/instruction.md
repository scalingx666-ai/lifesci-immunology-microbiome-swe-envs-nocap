# Issue

**Title:** Avoid std::exit() from a worker thread in fastq_mergepairs

## Description

## Problem

`fastq_mergepairs` processes read pairs with a pool of worker threads. Two
error paths reachable from a worker called `std::exit()` directly:

- `get_qual()` (reached from `process()` in the worker pool) on a FASTQ
  quality value outside `[fastq_qmin, fastq_qmax]`, and
- the "More forward reads than reverse reads" check in `read_pair()`.

Calling `std::exit()` from a worker is unsafe while sibling workers are still
running: `exit()` flushes and closes the shared output streams and runs static
destructors concurrently with threads that are still writing to those streams.
That is a data race on stdio/global teardown. It can corrupt libc state and
crash, and it can also drop the fatal message before it reaches the `--log`
file.

The crash is timing-dependent, so it is intermittent and platform-dependent: it
was observed as an intermittent `Illegal instruction (core dumped)` on FreeBSD
(clang libc), while the same race happens to be benign on glibc/Linux.

## Fix

Make the worker error path cooperative instead of exiting in place:

- A worker that detects the error records the first occurrence (reason and
  value) and sets an `std::atomic<bool>` abort flag.
- `process()`, the chunk-processing loop, and `pair_worker()` observe the flag
  and unwind; `finished_all` is set under the lock with a `notify_all()` so any
  parked worker wakes and exits.
- After the worker pool has joined, `pair_all()` reports the recorded error and
  calls `exit()` on the main thread. Teardown is then single-threaded, and the
  message reliably reaches both `stderr` and the `--log` file.

Output messages and exit status are unchanged.

## Testing

- Functional: out-of-range qmin/qmax still print the correct fatal message and
  exit non-zero; the `--log` message is now reliably present; the forward/reverse
  read-count mismatch is still reported; normal merging is unchanged.
- Stress: repeated multi-threaded runs over large inputs with an out-of-range
  value injected mid-stream, and a concurrent read-count-mismatch case — all
  clean exits, no crash or hang.
- A ThreadSanitizer build reported no data races on the abort or normal paths.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0dac0396ba22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.