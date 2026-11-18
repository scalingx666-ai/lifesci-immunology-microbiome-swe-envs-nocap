# Issue

**Title:** Create `--disk-swap` temp files for a column only when its buffer overflows

## Description

With `--disk-swap`, `annotate` created a temporary directory and a disk-backed sorter for every new label, even for a label with a few dozen set bits. That costs about 0.1 s per label. Inputs with many small labels spent almost all their time there.

`bitmap_builder_set_disk` now keeps the positions in memory. It moves them to disk only once the buffer is full and its distinct positions take more than half of it. The buffer size and the output are unchanged.

Measured with `annotate --anno-header --cache 128 --mem-cap-gb 0.01 -p 24 --disk-swap` on 100,000 records with 4,095 labels. Query results are the same.

| | master | this PR |
|---|---|---|
| time | 459 s | 4.6 s |
| temporary directories | 4,095 | 0 |

Columns that overflow the buffer still go to disk. A run with `--mem-cap-gb 0.000001` created 184 temporary directories and gave the same query results as master.

Prepared with AI assistance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8ca5aa16b35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.