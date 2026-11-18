# Issue

**Title:** Fix segfaults in #10

## Description

I was able to track down the issue underlying the segfaults reported by me in #10; in both cases,
wrong `mmap()` usage was the culprit, assuming that both input as well as database files would
always be writable by the user executing Metabuli.

I switched the mapping of the input FASTA file to a readonly mapping, and introduced a new
`mode = 3` for `mmapData` with `MAP_PRIVATE` to be used with database files, so in-memory
changes aren't persisted to disk.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06bda08b0113`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.