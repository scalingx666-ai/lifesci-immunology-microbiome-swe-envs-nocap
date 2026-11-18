# Issue

**Title:** Output Bootstraps for assignTaxonomy

## Description

This is the code I worked up for #124

I did not modify the C function because the `assignment` variable returned by it already contained all the taxa assignments and bootstrap values before minBoot filtering.

I added the `outputBootstraps` to handle the logic of what to return. I am new to R and wasn't quite sure the best way to return two matrices, is returning a list of them the way you want it?

I return all the bootstrap values even if the taxa gets trimmed that way you can see if it was borderline passing or not.

```
> at90 <- assignTaxonomy(seqtab.nochim, "rdp_train_set_14.fa.gz", minBoot=90, outputBootstraps=TRUE)
> at90[[1]][213,]
     Kingdom       Phylum        Class        Order       Family        Genus
  "Bacteria" "Firmicutes"           NA           NA           NA           NA
> at90[[2]][213,]
Kingdom  Phylum   Class   Order  Family   Genus
    100      90      73      73       8       8
>
```

I would be happy to make any fixes needed!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e0806f08491`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.