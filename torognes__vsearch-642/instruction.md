# Issue

**Title:** Fix two heap out-of-bounds bugs in fastq_eestats; report a friendly out-of-memory error

## Description

This addresses two reachable heap out-of-bounds bugs in `fastq_eestats` and
improves the error message when a C++ allocation fails.

### 1. 32-bit overflow in `ee_start()` for long reads → heap OOB

`ee_start()` computed `pos * ((resolution * (pos + 1)) + 2) / 2` entirely in
32-bit `int` (every operand is `int`) and only widened the *result* to the
`int64_t` return type. With the default `resolution` (1000) the value grows
~`500·pos²` and exceeds `INT_MAX` once `pos ≳ 2074`. The overflowed value is
used both to size `ee_length_table` and to index it, so for reads longer than
~2074 bp (routine for PacBio/Nanopore and merged amplicons) the allocation size
and the indices disagree, giving out-of-bounds heap reads and writes.

Fix: take `pos` as `int64_t` so the arithmetic is performed in 64-bit. All four
call sites already pass `int64_t` lengths, which were previously narrowed to the
`int` parameter, so this also removes that narrowing.

### 2. Per-position quality-row overflow when `--fastq_qmin ≥ 2` → heap OOB write

Each per-position row of `qual_length_table` has width `max_quality + 1`, where
`max_quality` was `opt_fastq_qmax - opt_fastq_qmin + 1`, so valid in-row indices
were `0 … qmax - qmin + 1`. But the write used the **raw** quality value as the
index (`++qual_length_table[((max_quality + 1) * i) + qual]`, with
`qual ∈ [qmin, qmax]`). When `qmin > 1`, a high-quality base indexes up to
`qmin - 1` slots past its row, corrupting the next position's row and, at the
last position, writing past the whole allocation — e.g.
`fastq_eestats f.fastq --output o --fastq_qmin 10` on data with near-`qmax`
scores.

Fix: size the rows by `qmax` (`max_quality = opt_fastq_qmax + 1`). The reader
loops already treat the row index as the quality value itself, so no reader
change is needed, and the default `qmin = 0` layout is byte-for-byte identical.

### 3. Friendly message on failed C++ allocations

`xmalloc()` reports a clean "Unable to allocate enough memory." via `fatal()`
when `malloc` returns null, but C++ allocations (`std::vector`, `std::string`,
…) go through `operator new`, which throws `std::bad_alloc` on failure. Because
the code is compiled with `-fno-exceptions`, that exception cannot be caught and
instead calls `std::terminate()`/`abort()` — e.g. `fastq_eestats` on a long read
prints "terminate called after throwing an instance of 'std::bad_alloc'" and
aborts with SIGABRT.

A `std::set_new_handler` is installed at CLI startup that emits the same friendly
message and exits with `EXIT_FAILURE`. The handler runs under memory exhaustion,
so it does not allocate: it writes a fixed string with `write(2)` and leaves via
`_exit()` without touching stdio. It is installed only in the CLI (inside the
`VSEARCH_NO_MAIN` guard), leaving the library API to manage its own handler.
This recovers a clean message for a refused allocation (`operator new` returns
null); it cannot intercept a kernel OOM kill of an overcommitted allocation.

### Verification

Built with `-fsanitize=address,undefined`:

- The quality-row overflow reproduces as a heap-buffer-overflow WRITE under ASan
  (`--fastq_qmin 30` on near-`qmax` data) before the fix, and runs clean after.
- The `ee_start()` overflow was confirmed with an old-vs-new check (the old form
  goes negative/wrong at `pos ≳ 2000`; the new form is correct in 64-bit).
- Under a virtual-memory limit, a failed allocation now prints
  "Fatal error: Unable to allocate enough memory." and exits 1, instead of the
  `std::bad_alloc`/`terminate` abort.
- Default-option output is unchanged; full build (`make ARFLAGS="cr"`) succeeds
  with no new warnings under `-Wall -Wextra -Wpedantic`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbb96e6c5d76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.