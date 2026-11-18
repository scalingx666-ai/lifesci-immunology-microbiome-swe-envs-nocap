# Issue

**Title:** Add standalone CLI options

## Description

Adds two scripts `empress tree-plot` and `empress community-plot`

## Important changes:

- Added a `q2` flag to `_plot_utils.save_viz` indicating whether to save with the QIIME2 specific stuff (defaults to True so nothing should change in existing tests).
- Moved some of the PCoA processing from `_plot.community_plot` to a new method `_plot_utils.prepare_pcoa`. This allows us to reuse this code for the standalone community plotting.
- Added a new file `_parameter_descriptions.py` (and modifies `plugin_setup.py` accordingly) to clean up the process of assigning parameter descriptions to both the QIIME2 and standalone versions of commands.

## Current status:

- [x] Scripts added
- [x] Documentation updated
- [x] Parameter descriptions (i.e. `--help`)
- [x] CLI tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1563ae251482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.