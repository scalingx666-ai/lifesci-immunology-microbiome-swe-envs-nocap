# Issue

**Title:** Update strobealign index to format version 5 for strobealign 0.17.0

## Description

Regenerated tests/data/7seqs.fna.r100.sti using strobealign 0.17.0, which
writes index format version 5. The old index was version 3, incompatible
with strobealign >=0.17.0, causing test_strobealign_pregenerated_index to fail.

Also bumped the minimum strobealign version in pixi.toml to >=0.17.0 to
match the index format.

Claude-Session: https://claude.ai/code/session_01BUkWFEp9YRYAVwvVDFudGU

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `789b2f064655`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.