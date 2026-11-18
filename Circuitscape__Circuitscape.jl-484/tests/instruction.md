# Issue

**Title:** Implement reclass tables

## Description

.

`use_reclass_table` / `reclass_file` have been parsed and documented as *not yet implemented* since the port. The use case from the issue — fitting many resistance parameterisations to one large raster without exporting a new multi-GB file each time — is what the option existed for in Circuitscape 4.

**Format**: two whitespace-separated columns, `old new`, one pair per line. Every habitat cell whose value equals `old` is set to `new`, before the resistance ↔ conductance conversion, so the table is written in the same units as the raster. Cells not mentioned (including NODATA) are untouched. A table that is not two columns is rejected by name.

**Single pass**: replacement is one `Dict` lookup per cell, so chained rows (`1 2` then `2 3`) send 1 to 2, not to 3 — the compounding bug vlandau identified in the Python original's sequential loop. Same approach as the Omniscape implementation he linked.

Raster mode only (network graphs have no habitat raster). Docs section updated with the format.

**Tests**: unit test for the no-compounding property and the column check; end-to-end pairwise run showing that a table doubling every resistance doubles every effective resistance, and that a table naming absent values is a no-op. Full suite passes locally (Unit 21/21, CG+AMG 719, CHOLMOD 719, Issue 341 46).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3fb63980a34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.