# Issue

**Title:** Implement set_focal_node_currents_to_zero

## Description

.

`set_focal_node_currents_to_zero` has been parsed, written back into the output INI and documented as *not yet implemented* since the port — a user setting it got no signal that nothing happened.

**Pairwise**: in `write_cur_maps`, the cells whose local node index is one of the two focal nodes being solved are zeroed in that pair's current map before it is processed, accumulated and written. Focal regions collapse to a single node, so the whole region is cleared. Cumulative maps therefore show only current that flows *through* a focal region when other pairs are active (Dickson et al. 2013).

**One-to-all / all-to-one**: every focal node is active on each solve (one as source, the rest as grounds), so all focal cells are zeroed in `advanced_kernel` before the per-point map is written and returned for accumulation.

Applies to raster current maps; network node currents are unaffected. Resistances are unchanged. Advanced mode has no focal nodes and ignores the flag, as in Circuitscape 4.

`OutputFlags` gains a field; the only other constructor (`compute_omniscape_current`) is updated. Docs: the *not yet implemented* note is replaced with the actual behaviour.

**Tests**: 5×5 grid with a two-cell focal region and two single-cell nodes. Checks that the active pair's cells are zero in the pair map, the inactive node's cell is untouched, all other cells are identical to the unflagged run, resistances are identical, the cumulative map is strictly smaller at every focal cell and identical elsewhere, and that one-to-all zeroes every focal cell.

Full suite passes locally (Unit 26/26, CG+AMG 719, CHOLMOD 719, Issue 341 46).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad23013b5026`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.