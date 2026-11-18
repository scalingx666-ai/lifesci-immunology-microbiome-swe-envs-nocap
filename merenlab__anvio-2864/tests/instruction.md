# Issue

**Title:** Fix colorbar keys in `anvi-draw-kegg-pathways` HTML map player

## Description

This PR affects colorbar keys in HTML map players produced using the `--animate-files-by-map` flag.
- Maintain the original aspect ratio of colorbar images displayed in the key column on the right side of the player.
- Only show border colorbars on maps that can color border rings. These appeared in the key column for every map if rings were colored. Now neither reaction nor compound border colorbars appear for global maps, where rings cannot be drawn, and reaction border colorbars do not appear for overview maps, where rings can be drawn on compound circles but not reaction lines.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5711fcd59555`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.