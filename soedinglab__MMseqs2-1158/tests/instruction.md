# Issue

**Title:** Advise huge pages for memory mapped databases

## Description

`MADV_HUGEPAGE` on the mmap in `DBReader` and `MemoryMapped` (`touchdb`). If the advising mapping reads a file first, the page cache keeps it in huge pages (large folio support, e.g. ext4 since 6.16, xfs) and later processes reuse them.

Single query prefilter process against a 10M sequence `db.idx` loaded by `touchdb`, `--db-load-mode 2`, GB10:

| | wall | minor faults |
|---|---|---|
| before | 0.58s | 175k |
| after | 0.05s | 21k |

A file already cached in small pages stays so until evicted. Hits are identical.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcf516aba34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.