# Issue

**Title:** Remake hostremoval

## Description

- Added speedup to filtering of hostreads via minimap2
- Added option to speed up minimap2 alignment for references (not host removal) by providing the `mmap2_fraction_filter` and `mmap2_window` parameters
- Update Tower yaml to find individual aligner bamfiles
- Change sort to be piped from aligner rather than separate modules to save on space/intermediate files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2250064a013b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.