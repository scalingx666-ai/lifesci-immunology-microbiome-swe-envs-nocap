# Issue

**Title:** Changing metaphlan2krona.py to stop at the species level and fixes parsing errors with latest 4.2.* format

## Description

Hi,

The current metaphlan2krona.py script currently fails for some profile outputs from the current 4.2.* versions of metaphlan.
In some cases, there are multiple lineages on one line (this should probably be fixed in a separate PR), and the abundance is not extracted properly.

This PR fixes this by stopping at the 't__' lines, and I changed the logic for how to extract the abundances and lineages.
I also changed the order so it's easier to use the file with the Krona script ktImportTaxonomy.sh.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3a649773f07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.