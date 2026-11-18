# Issue

**Title:** Add `--max-window-length` parameter for discov

## Description

This PR introduces a new flag to both `anvi-profile-blitz` and `anvi-summarize` that impacts the discov calculation. `--max-window-length` is the opposite of the existing parameter `--min-window-length` and further restricts the set of window lengths that are used for percentage-based windows. That is, it only affects calculations when `--window-length-as-percentage` is used as the window-sizing strategy (which is the default for contig-level stats).

**Why is this necessary?**
The window length affects the discov calculation -- longer windows make discov more coarse while shorter windows make it more fine. Therefore, discov scores computed using very different window lengths are not very comparable. Previously, percentage-based discov scores on contigs or genomes with very wide size distributions will include some scores computed using very small windows and some using huge windows, making it difficult to set thresholds for determining presence absence.

The new flag mitigates this issue somewhat by limiting the range of window sizes in percentage-based calculations. Discov computed with 300bp windows is still not very comparable to discov computed with 10,000bp windows, but it is a lot better than comparing to discov computed with 90,000bp windows.

With the default percentage-based sizing parameters of 1% with minimum 300 and maximum 10,000:
- any contig < ~30 kb will have 300bp windows
- any contig >= ~30 kb and < ~1 Mb will have variable window sizes within the range
- any contig >~1 Mb will have 10,000bp windows

If a user wants no minimum length, they can pass `--min-window-length 0`, and if a user wants no maximum length, they can pass `--max-window-length 0` (the code treats a max of 0 as unbounded, since there is no way to pass NA values to this argument and not adding the flag treats it as a None, which gets the current default of 10kb).

I still need to test this a bit more thoroughly to see the effect, so this PR should not be merged yet.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b472ba0bd4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.