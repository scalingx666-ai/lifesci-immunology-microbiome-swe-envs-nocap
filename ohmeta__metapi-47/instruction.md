# Issue

**Title:** deepvirfinder now added to checkv

## Description

- Revise identify_multi.smk to distribute the dvf identified viral contigs (the same logic as that for dbscan_swa):
    1. extract dvf identified viral contigs
    2. distribute the them back to each assembly group under 06.identify
    3. these can then be checked by checkv

- config.yaml has been updated accordingly

- annotation.smk has been updated
    1. I/O for distribution optimized (open the output file once only)
    2. output revised and now check(v)_all works

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ceca8fc08da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.