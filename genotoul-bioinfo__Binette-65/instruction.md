# Issue

**Title:** Rewrite FASTA writing function without pyfastx index

## Description

This PR replaces the previous function used to write final bin FASTA files, which relied on pyfastx index, with a custom implementation using pyfastx.Fastx (no index) and a buffering strategy.

Instead of loading all sequences into memory or opening a large number of files at once, the new version:

- Streams through the input FASTA file with pyfastx.Fastx
- Buffers output entries per bin based on total character size
- Periodically flushes the buffer to disk

This should fix the `corrupted size vs. prev_size` error reported in #58 as pyfastx index is not beeing used in Binette anymore.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `947d05d35faa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.