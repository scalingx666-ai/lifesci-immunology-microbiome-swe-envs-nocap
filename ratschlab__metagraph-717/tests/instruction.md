# Issue

**Title:** Keep sparse annotation columns sparse during updates and merging

## Description

`merge_anno` turns every label that appears in more than one input into a dense bitmap. With billions of rows, each such column takes gigabytes. This PR keeps these columns sparse and merges them directly.

- Evicted sparse columns stay editable as sets of positions. Updates no longer allocate dense bitmaps.
- Files are merged in one pass. Independent labels are merged in parallel, each under its own lock.
- Small sparse unions, up to 65,536 set bits, are decoded into a buffer. Larger ones are counted first and then built straight into the compressed column, so memory does not grow with column size.
- Dense columns still go through the existing cache. The file format is unchanged.

Measured with the `merge_anno` CLI, both builds with the same flags. Outputs are byte-identical.

| Input | master | this PR |
|---|---|---|
| GnomAD chrY + chr21, 29 labels, 1 thread | 134 s, 39.3 GiB | 62 s, 5.8 GiB |
| UHGG pilot, 17 files, 51,770 shared labels | not finished after 20 min | 5.5 s (1 thread), 2.4 s (8 threads), 0.37 GB |

GnomAD: one master run, 4 runs of this PR (62–65 s). UHGG: median of 5 runs.

Prepared with AI assistance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9a5dc06f999`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.