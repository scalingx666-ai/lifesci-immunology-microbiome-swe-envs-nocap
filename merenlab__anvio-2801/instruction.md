# Issue

**Title:** fix negative start position in keep-promoter mode of anvi-gen-pan-representative

## Description

**Description:**
---
In keep-promoter mode, `anvi-gen-pan-representative` includes the flanking region of the target sequence (one or more genes) when extracting genes to build the supplementary contig. This means instead of extracting the sequence from the start position of the first target gene, it actually extracts from the stop position of the preceding gene.

**Bug:**
---
When the preceding gene overlaps the first target gene, its stop position falls after the target gene's start. Once coordinates are recalculated relative to the extraction start, the first gene's start position becomes negative.

**Fix:**
---
Set the start position to the lower of the two values: the preceding gene's stop or the first target gene's start. If no preceding gene exists, the target sequence is at the start of a contig, so the start position is 0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ecf59f1fabbc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.