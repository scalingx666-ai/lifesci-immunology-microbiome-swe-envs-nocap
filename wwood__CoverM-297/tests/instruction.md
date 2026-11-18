# Issue

**Title:** Add rammap as a supported read mapping program

## Description

## Summary
This PR adds support for [rammap](https://github.com/jwanglab/rammap), a minimap2-compatible read aligner, as a mapping option in CoverM alongside existing mappers like bwa-mem, minimap2, and strobealign.

## Key Changes

- **Added rammap to the mapping software list** in CLI configuration with appropriate help text describing it as "a minimap2-compatible aligner" with the `-x sr` preset
- **Implemented rammap command building** with the command template `rammap -x sr -a` (short-read preset with SAM output)
- **Added `--rammap-params` CLI option** to allow users to specify additional parameters, with the same security warnings as other mapping tools
- **Integrated rammap into the mapping program enum** (`MappingProgram::RAMMAP`) and updated all relevant match statements across the codebase
- **Added rammap version checking** (requires v1.1.1+) via `check_for_rammap()` function
- **Updated mapping index handling** to skip pre-indexing for rammap (not yet supported) with appropriate logging
- **Added test case** (`test_make_rammap`) to verify rammap mapping functionality works end-to-end
- **Updated documentation** in README.md and pixi.toml to include rammap as a dependency

## Implementation Details

- Rammap is treated similarly to minimap2 in terms of read format handling (auto-detects interleaved input based on read names)
- Like strobealign, rammap does not require separate log file handling for minimap2 compatibility
- The implementation follows the existing pattern for adding new mapping programs, ensuring consistency with the codebase architecture
- Rammap requires the reference to be specified (consistent with other mappers)

https://claude.ai/code/session_01D4S2TfmfT9BsYgJF5VDz81

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `feec618cdf0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.