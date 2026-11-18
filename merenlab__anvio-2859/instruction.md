# Issue

**Title:** Count each accession of a map element once in `anvi-draw-kegg-pathways`

## Description

Some KGML entries name the same accession twice. `anvi-draw-kegg-pathways` kept the duplicate when it reduced an element's accessions to one value, so aggregations such as `sum` and `count` counted that accession twice, and `mean` weighted it twice.

- Entry 179 of ko00670 has `reaction="rn:R08557 rn:R08557"`. With a reaction file that gives R08557 a value of 3, the element was colored as 6.
- Five compound entries of ko04976 (bile secretion) name a compound twice: 144, 150, 165, 167, and 226. In entry 144, C05122 and C01921 with a value of 1 each summed to 4 rather than 2.
- No ortholog entry names a KO twice, so maps drawn from KOs are unchanged.

`_get_entry_kegg_ids` now returns each accession once, in the order it first appears. The categorical path removed duplicates on its own and now relies on this instead. Only the values of the six elements above change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1eccd7dd6959`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.