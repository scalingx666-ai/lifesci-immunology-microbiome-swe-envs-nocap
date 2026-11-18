# Issue

**Title:** Document optional mapper installation requirements

## Description

## Summary
Addresses #303: makes it clear that the bioconda package installs only the default mappers, so the others must be installed separately. Also fixes a strobealign 0.18 test failure in the unlocked CI job.

## Key Changes
- **README.md**:
  - The bioconda section now lists what the package includes: strobealign, minimap2, bwa, samtools, skani and FastANI. It explains how to install the optional mappers (bwa-mem2, minibwa, rammap) separately.
  - The dependencies list marks strobealign as the default mapper and adds bwa and minibwa. A note says which mappers bioconda installs.
- **src/cli.rs**: a shared `bioconda_mappers_note()` is added to the `-p/--mapper` help of `genome`, `contig`, `make` and `makedb`. The HTML in `docs/` will pick it up at the next release.
- **tests/test_cmdline.rs**: `test_sharded_contig_input_reads_strobealign` now accepts either the pre-0.18 or the strobealign 0.18.0 output. 0.18.0 gives slightly different mean coverages, which failed the `test_dependencies_optimistic` job.

## Bioconda recipe check
The current recipe (0.8.0) already includes the default mappers: strobealign (default for `genome`/`contig`), minimap2 (default for `makedb`) and bwa. It also has skani, the default dereplication precluster method. No change is needed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_011bFQk8BPxzNCS67jkdFGRQ

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5501168b1438`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.