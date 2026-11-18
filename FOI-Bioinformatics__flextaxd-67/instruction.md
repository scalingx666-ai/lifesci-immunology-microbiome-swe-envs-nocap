# Issue

**Title:** added --purge_database functionality to purge a FTD from genomes that…

## Description

… are missing (including tree nodes and superfluous parent nodes)

More detailed specification about the implementation:
- It gets the nodes for these genomes and then traverses the tables of the FlexTaxD-database, removing entries (e.g. parent-relations) that are exclusive to such nodes. It tests so that any parent node is not a parent for a node that is not deleted.
- Optionally, missing genomes that have no distinct nodes in the tree can be removed (force_genome_delete).
  - This occurs when using GTDB taxonomy (full GTDB-database) but only using the representative genomes.
  - The nodes of such datasets have multiple children, of which one is the representative genome and the other children can be removed.
  - When this flag is applied, the function will remove missing entries from all tables wherever possible ("truly missing" datasets) in addition to naively removing all missing genomes (datasets that are missing due to exhaustive import of taxonomy information, such as import from GTDB)

Also made minor changes to user interaction related to missing genomes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a25f0305da42`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.