# Issue

**Title:** summarise: Add --output-cami-iii-gtdb-profile

## Description

## Summary
- Adds `--output-cami-iii-gtdb-profile` to `summarise`, converting a taxonomic profile into the [CAMI III GTDB taxonomic profiling format](https://cami-challenge.org/file-formats/#taxonomic-profiling) for comparison against other profilers with e.g. OPAL. Requires `--input-taxonomic-profiles`.
- Percentages are relative abundances of each taxon's filled coverage. GTDB taxon names stand in for NCBI taxonomy IDs, since the format is GTDB-based.
- Viral profiles are rejected, as the format assumes GTDB bacterial/archaeal ranks and taxonomy.

The only addition to `condense.py` is `CondensedCommunityProfileCamiIiiGtdbWriter`, which takes an open IO handle to match the other summariser writers; `Condenser.condense` is untouched. Only the hand-written `docs/preludes/summarise_prelude.md` is updated — `docs/tools/summarise.md` is generated at release.

## Test plan
- [x] `pytest test/test_summariser.py test/test_condense.py` — 46 passed, 1 skipped
- [x] `pytest test/test_condense_viral.py`, and `test/test_pipe.py -k "profile or diamond_assignment"` — pass (full `test_pipe.py` not run)
- [x] New CLI tests covering the conversion output, the missing-`--input-taxonomic-profiles` error, and viral rejection
- [x] Confirmed the option text added to the prelude matches what `summarise --full-help-roff` generates

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24552d6562d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.