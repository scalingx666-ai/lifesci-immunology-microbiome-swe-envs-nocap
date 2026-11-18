# Issue

**Title:** Fix integer truncation of sequence/header lengths above INT_MAX (~2 GB)

## Description

## Summary

Several code paths carry a 64-bit sequence or header length in an `int`, which
truncates (often to a negative value) once a single sequence or header exceeds
`INT_MAX` (~2 GB). Depending on the site this either overflows a buffer (a
too-small buffer is allocated, then written past) or produces wrong/garbled
output. Such records are rare but occur on genuinely large data (large
assemblies, long single sequences), not crafted input. This change carries the
lengths as 64-bit / `size_t` where they size buffers or drive copies, and guards
the one place where a wider type isn't practical.

## Changes

- **getseq (`test_label_match`)**: `field_buffer_size` and the field/header/word
  lengths were computed in `int`; a >2 GB header, label, `--label_field`, or
  `--label_word` made them negative, driving an undersized buffer that
  `strcpy`/`std::copy` then overran. Now carried as `size_t`.
- **results / showalign (`--rowlen 0`)**: with `--rowlen 0` the alignment block
  width is the whole alignment; it was summed into an `int` that sized the output
  line buffers while the writer walked the full 64-bit width, overrunning them
  for >2 GB alignments. The row length and `align_show`'s width parameter are now
  `int64_t`.
- **otutable (`otutable_add`)**: the sample/OTU/taxonomy name lengths (from
  `strspn`/`strcspn`/regex) were `int`, giving an undersized `resize()` and a
  backwards `std::copy` for >2 GB headers. Now `size_t`.
- **fasta (`fasta_print_sequence`)**: a >2 GB sequence printed garbage (negative
  `%.*s` precision) or was silently truncated (the fold loop never ran). The
  linearized path now uses `fwrite` (a single `%.*s` precision is an `int` and
  cannot express the length) and the fold loop uses a 64-bit counter.
- **fastx (`fastx_filter_header`)**: header lengths feed `int` fields in the
  per-query search state shared across many commands, which aren't cheap to
  widen. A header longer than `INT_MAX - 2001` is now rejected at the single
  point all FASTA/FASTQ (and database) reads pass through — mirroring the
  existing illegal-character handling (recorded as a deferred error on worker
  threads and reported from the main thread, fatal otherwise) — instead of
  overflowing the per-query header buffer.
- **Comments**: record the remaining `int` sequence-length limit in
  `fasta_print_general` / `fastq_print_general`, and why the database index
  keeps 32-bit length fields (the `--maxseqlength` cap is `UINT32_MAX`).

## Testing

Default (`-O2`) and a `-Wconversion -Wsign-conversion` debug build are clean.
Output is byte-identical for normal-length inputs, verified across
`--fastx_getseqs` (`--label_word`/`--label_words` + `--label_field`), `--alnout`
(default / `--rowlen 0` / small `--rowlen`), `--otutabout`/`--biomout`, and FASTA
output (folded and linearized), including under `_GLIBCXX_DEBUG`. The >2 GB
trigger itself is impractical to exercise in CI.

## Note

This guards the header path. The analogous query-*sequence* length (allowed up
to `UINT32_MAX` via `--maxseqlength`, above `INT_MAX`) still narrows to `int` in
the search engine, so a 2–4.29 GB query sequence remains affected. A natural
follow-up is to lower the `--maxseqlength` hard cap to `INT_MAX`, which would
make every sequence-length narrowing safe by construction (the int-based aligner
cannot process longer sequences regardless).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47fcfc3a58b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.