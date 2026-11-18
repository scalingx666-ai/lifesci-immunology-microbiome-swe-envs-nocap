# Issue

**Title:** MRG: handle (ignore) empty taxids for `bioboxes` format

## Description

- bioboxes format relies on having a `taxid`, so it fails with empty/missing `taxids`. Some NCBI lineages have missing/empty internal tax ranks, e.g. order, genus, etc. Here we ignore (do not print) results from empty taxids, which allows us to bypass these problematic ranks and still get output from the classifiable ranks.

example taxonomy with missing ranks (lineage from an older CAMI db):

```
GCF_003480425.1,2292892,2|1239|||||2292892|,Bacteria,Firmicutes,unclassified Firmicutes class,unclassified Firmicutes order,unclassified Firmicutes family,unclassified Firmicutes genus,Firmicutes bacterium AM31-12AC,unclassified Firmicutes bacterium AM31-12AC subspecies/strain
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7946469d26a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.