# Issue

**Title:** Harden the UDB reader against corrupt or crafted files

## Description

## Summary

`udb_read()` trusted several values read verbatim from a `.udb` file and used
them as allocation sizes, loop bounds, or indices without validation, so a
corrupt or crafted database could drive out-of-bounds memory access. This adds
the missing bounds checks; valid databases are unaffected.

Two commits:

### 1. Validate UDB fields on load
- **Sequence numbers (`kmerindex`).** Each entry is used both as a bit offset in
  `bitmap_set()` (which writes `bitmap[value >> 3]` with no bounds check) and as
  an index into `seqindex`/`dbindex_map` during search. A value `>= seqcount` was
  therefore a near-arbitrary out-of-bounds heap write (with bitmaps enabled) or
  read. Every entry is now rejected unless `< seqcount`, right after the section
  is read.
- **`kmerindexsize`.** It is accumulated from the per-word `kmercount[]` values
  with no consistency check. The running sum is now overflow-checked and rejected
  if it exceeds `filesize / 4` (the word list stores 4 bytes per entry, so a
  larger total cannot match the file).
- **`datap` allocation.** `xmalloc(udb_headerchars + nucleotides + seqcount)`
  summed three file-derived 64-bit values with no overflow guard; the addition
  now goes through an overflow-checked helper.

### 2. Tighten header-index validation
- Header offsets were only required to be non-decreasing, so two equal
  consecutive offsets slipped through and made `headerlen = next - current - 1`
  underflow to ~4 GB. Offsets are now required to strictly increase.
- `seqcount` was only checked `!= 0`; it is now bounded by `filesize / 4`, which
  also closes a `seqcount + 1` wrap at `UINT_MAX` when the header-index vector is
  sized.

## Verification

- A `makeudb_usearch` → `usearch_global` / `cluster_fast` round-trip on valid
  data produces unchanged results (exit 0).
- Crafted databases — an inflated `kmerindex[0]`, an inflated `kmercount[0]`, and
  equal consecutive header offsets — now fail with a clear `Invalid UDB file`
  (exit 1).
- Builds clean under `-O2` and `--enable-debug` (including
  `-Wconversion`/`-Wsign-conversion`).

These triggers need multi-GB or deliberately malformed inputs and aren't part of
the normal test suite; verification is by code review plus the round-trip above.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fe9e4cfb252`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.