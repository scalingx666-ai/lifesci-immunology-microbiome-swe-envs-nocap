# Issue

**Title:** Fix SSHash build running out of open files

## Description

`build --graph sshash` failed with "cannot open file" on a 17.7 GB contig file at `-p 48` under the usual soft limit of 1024 open files.

**Cause.** Each SSHash build thread sorts minimizer tuples into run files of `RAM / (2 · 18 B · threads)`. The final merge opens and memory-maps every run at once. metagraph never set SSHash's RAM limit, so the default of 8 GiB applied: about 89.5 MB per run, roughly 1,000 runs for that input.

**Changes**
- SSHash bumped to ratschlab/sshash `9f0cbe5`. It merges at most `min(1024, soft RLIMIT_NOFILE / 2)` runs at a time, then does the final counting merge as before. The index is byte-identical, and there is no extra pass when the runs fit. New SSHash test: `test_merge_fan_in`.
- `--mem-cap-gb` now sets SSHash's construction RAM budget, but never below SSHash's 8 GiB default, because the build default of 1 would make runs smaller. A larger budget gives fewer, longer runs: at `--mem-cap-gb 300 -p 48` the input above writes 48 runs instead of about 1,023 (computed).
- At startup, `main()` raises the soft RLIMIT_NOFILE to the hard limit. That also helps the BOSS chunk merge, which sizes itself from `get_max_files_open()`.
- New integration test `test_build.py::test_sshash_low_soft_open_file_limit`: it runs `build --graph sshash -p 32` with the soft limit set to 24 and the hard limit unchanged.

**Before/after** (laptop, SSHash tool, salmonella_100 unitigs with 13.1 M k-mers, `-t 32 -g 1`, 3 repeats)

| build | ulimit -n | result | wall | max RSS | index md5 |
|---|---|---|---|---|---|
| before | 4096 | ok, 33 runs | 0.46 s | ~180 MB | b569fd2fa1b9 |
| before | 24 | crash: "cannot open file" | – | – | – |
| after | 4096 | ok, no extra round | 0.47 s | ~183 MB | b569fd2fa1b9 |
| after | 24 / 16 | ok, 32 → 3 / 4 runs, then final merge | 0.51 s | ~180 MB | b569fd2fa1b9 |

The old metagraph binary on the new integration test's inputs, with soft limit 24 and hard limit 524,288, exits with rc 134 "cannot open file". With soft 4096 it builds 591,997 nodes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
---
## Summary by cubic
Fixes SSHash graph builds failing with "cannot open file" on large inputs under the default 1024 open-file soft limit.

- Raises the soft `RLIMIT_NOFILE` to the hard limit at startup, warning if it fails; SSHash likewise raises it before merging, which also helps the BOSS chunk merge.
- Passes `--mem-cap-gb` to SSHash as its construction RAM budget, converted from GB to GiB and never below the 8 GiB default, so runs are fewer and longer; non-finite or negative values are ignored.
- Updates SSHash to merge at most half of `min(open files, vm.max_map_count)` runs at a time, so builds that fit stay single-pass and byte-identical.
- Adds integration tests building an SSHash graph under a low soft limit and under low soft and hard limits.

<sup>Written for commit f16ed79c901465a3551856ff21cfa014edded4d6. Summary will update on new commits.</sup>

<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/696?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/696?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F696&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>

<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7a7b1207cce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.