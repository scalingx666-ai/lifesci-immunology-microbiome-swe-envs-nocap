# Issue

**Title:** Fix four out-of-bounds reads/writes reachable with normal input

## Description

Four small, independent memory-safety fixes:

- **`fastx_getsubseq`** — bound the offset so `--subseq_start` past the sequence length no longer reads out of bounds (emits an empty subsequence).
- **`random_subsampling`** — stop reading one element past `seqindex` when fetching the next amplicon's abundance under `--sizein`.
- **clustering** — clamp the hit-list insertion bound so `--maxaccepts + --maxrejects` larger than the database can't overflow the `tophits` buffer.
- **SFF reader** — reject inverted clip regions and truncated flowgrams instead of desyncing; the file-derived overflow `assert()`s (compiled out under `NDEBUG`) now `fatal()`.

Each is reachable with ordinary data or a legitimate option choice; valid inputs are unaffected.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bbc5e6e8330`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.