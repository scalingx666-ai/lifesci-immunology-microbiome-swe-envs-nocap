# Issue

**Title:** Update annotate gff

## Description

Carried over changes and fixes from mettannotator:

- new parser for antiSMASH results
- ncRNAs separated into rRNA and ncRNA; ncRNA have class added to the 9th column of the final GFF file
- fixed product parsing for ncRNA
- CDS with antiFam hits are now removed from the final GFF file as these are likely spurious ORFs
- GFF format fixes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `191068b8d9ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.