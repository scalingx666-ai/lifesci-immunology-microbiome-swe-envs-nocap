# Issue

**Title:** (Re)calculating graph display based on genomes of interest

## Description

Genome subsetting in the interface was not recalculating the graph shown, and it was causing some headaches. This PR allows the interactive genome subsetting in `anvi-display-pan-graph`.

With these changes, @ahenoch's `rerun_state` function now rebuilds a graph-to-be-displayed by dropping nodes/edges not covered by the requested genomes from the main graph, and by recomputing edge weights etc, re-laying it out, and keeping track of updated node types at all types (so 'core' reflects 'core' within the genomes shown). None of these affect summaries and underlying real data. These changes are (currently) only for visualization purposes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e36be54857f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.