# Issue

**Title:** Fix/freebsd dev stdin db

## Description

On FreeBSD, reading `--db` from `/dev/stdin` (e.g. a reference database piped
into uchime_ref) aborted with "Fatal error: File type not recognized."

Before loading the database, `udb_detect_isudb()` peeks at the 4-byte UDB magic
number, relying on the subsequent reader to reopen the file from the start. That
reopen-rewind only works for regular files, so the peek was skipped for pipes —
but the check used `stat()` on the *path*, which on FreeBSD sees `/dev/stdin` as
a character device, not a FIFO. The peek then consumed the first 4 bytes, and
the FASTA reader saw a truncated stream. On Linux these paths resolve to FIFOs,
so the bug was FreeBSD-only.

Fix: `fstat()` the open descriptor instead of `stat()`-ing the path, and treat
any non-regular file as non-UDB, returning without consuming input. A companion
change makes the FASTA/FASTQ reader treat any non-regular file (not just FIFOs)
as a non-rewindable stream.

Verified with the issue-506 tests in `frederic-mahe/vsearch-tests` on FreeBSD;
Linux/macOS unaffected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f9a122facc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.