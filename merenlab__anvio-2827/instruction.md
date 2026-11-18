# Issue

**Title:** Catch clashes with reserved colors before drawing in `anvi-draw-kegg-pathways`

## Description

Before drawing, `anvi-draw-kegg-pathways` checks layer colors against the colors KEGG maps keep for unhighlighted elements. Some clashes got past that check. They were then caught by `kgml` partway through drawing, which left some files already written. This PR closes those gaps.

- **Centered scales with a single value.** When every value is the same and the scale is centered, the maps draw every element in the colormap's middle color. The check tested the top color instead. Each value scale's norm is now paired with its center. The check uses the middle color when the scale is centered and the top color otherwise.
  - This removes a false refusal. With Greys and a center, the run was refused for #000000, but every element would have been drawn #959595.
  - It also catches the reverse case before drawing. With `Greys 0 0.01` and a center, the middle color is reserved but the top color is not.
- **Compound colors derived from reactions.** On global and overview maps drawn without a compound layer, each compound takes its color from the reactions it touches. That color was never checked.
  - A quick test first asks whether any reaction color or colormap could produce a reserved compound color at all. Usually none can, and the check stops there.
  - Otherwise, only the maps that can clash are colored without being drawn. A clash is refused before any file is written.
  - The error names the option to change: `--reaction-colormap`, `--reaction-category-colormap`, `--reaction-color`, the category colors file, or `--group-colormap`.
- **Single-color runs** of one contigs database or one reaction network now run both checks. Before, they had no reserved color check.
- **Refactors.** The staging loop of `_draw_map_elements` is now `_stage_map_elements`. The presence specs are built by `_element_presence_specs`. The per-category specs are built once by `_category_specs`. The check and the drawing therefore use the same colors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dc36603ff46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.