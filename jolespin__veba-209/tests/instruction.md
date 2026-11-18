# Issue

**Title:** Remove prepend-de-Bruijn support

## Description

## Summary

, where the `assembly` module crashes when run with **rnaSPAdes**. The SPAdes branch of `get_assembly_cmd()` unconditionally ran `prepend_de-bruijn_path.py` against `scaffolds.paths`, but rnaSPAdes writes `transcripts.paths` instead, so the step failed on a missing file.

Per the suggestion on the issue, this removes the prepend-de-Bruijn feature entirely rather than just patching the rnaSPAdes case. `prepend_de-bruijn_path.py` existed only to rewrite de Bruijn graph node IDs so they matched VEBA's sample-prefixed contigs. Its sole consumer was **MetaCoAG**, which was dropped from the default binner set in v2025.4.4 and is already slated for full removal in v2.6.0. No other part of the pipeline reads these graph/paths files.

## Changes

- **`bin/assembly.py`** — removed the SPAdes `scaffolds.paths` prefixing block from `get_assembly_cmd()`, and removed the script from `accessory_scripts` in `add_executables_to_environment()`.
- **`bin/assembly-long.py`** — removed both Flye prefixing blocks (`assembly_graph.gfa` and `assembly_info.txt`) from `get_assembly_cmd()`, and removed the script from `accessory_scripts`.
- **`bin/scripts/prepend_de-bruijn_path.py`** — deleted (no remaining callers).
- **`bin/VEBA_SCRIPT_VERSIONS`** — removed the manifest entry.
- **`CHANGELOG.md`** — documented the removal under `[2.6.0]`.

## Notes / impact

- The native assembler outputs (`scaffolds.paths`, `assembly_graph.gfa`, `assembly_info.txt`) are still produced by SPAdes/Flye and still symlinked to the final output. They simply keep their original, unprefixed node IDs.
- **MetaCoAG itself is left selectable** (its `--metacoag_*` arguments and wiring in the binning modules are untouched). **Fully removing MetaCoAG remains the separate, already-planned v2.6.0 task**. A user explicitly selecting `metacoag` would now get unprefixed graph IDs — acceptable given its deprecated status.

## Verification

- Both assembly modules parse cleanly (`ast.parse`).
- `grep -rn "prepend_de-bruijn" bin/` returns no matches.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `525d78d42a0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.