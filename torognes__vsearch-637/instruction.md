# Issue

**Title:** Fix a data race in uchime_ref and remove a dead, racy scorematrix global

## Description

Two small, independent thread-safety fixes in the alignment/chimera code,
both surfaced by a ThreadSanitizer run of the test suite.

## 1. Data race on the query file position in `uchime_ref`

In `chimera_thread_core`, the `uchime_ref` path read the query-file progress
position with `fasta_get_position(query_fasta_h)` while holding `mutex_output`,
but another worker advances the *same* shared handle in `fasta_next()` — which
writes `file_position` via `fastx_file_fill_buffer()` — while holding
`mutex_input`. The two accesses to `file_position` were serialized by *different*
mutexes, so they raced.

Fix: capture the position into a worker-local immediately after `fasta_next()`,
**under `mutex_input`**, and assign the shared `progress` counter from that local
under `mutex_output` — matching how `search` and `sintax` already capture
progress inside the input lock. The reported progress value is unchanged.

## 2. Remove the unused file-scope `scorematrix` in `align_simd`

The file-static `scorematrix` array was written by `search16_init()` but never
read (the aligner uses the per-instance `s->matrix`). The write was dead, and
because `search16_init()` runs inside the worker threads on the chimera path,
multiple workers wrote the shared global concurrently — a race on a value nobody
consumes. Dropping the global and its lone write removes both the dead store and
the race, with no behavioral change.

## Testing

- Builds cleanly (`-O2`).
- A ThreadSanitizer build over repeated `uchime_ref` runs reports no races after
  the fixes; alignment output is unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e9e84eb4244`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.