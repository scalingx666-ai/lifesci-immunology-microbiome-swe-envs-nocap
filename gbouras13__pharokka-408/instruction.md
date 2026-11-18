# Issue

**Title:** Genbank compatibility

## Description

Hi George,

This pull request handles the issue with coordinates of partial CDS features (sort of). So, BCBio's `GFF.parse()` can not handle strings as `start` and `stop` locations and also biopython's `Seqio.write("genbank")` requires integers for `start` and `stop`. I therefore decided to add the `partial` attribute from `pyrodigal` output to the Genbank file and handle the partial CDS coordinates on `suvtk`'s `gbk2tbl` end. I think this should not make a difference for using the gbk file as input to `phold`, but that should be checked (I will also review `phold`'s code to see if this `partial` attribute is retained in the final output).

I did fix the coordinate for partial CDS in `pharokka`'s feature table output so users can also just use this as input for `suvtk`. I still have to review GenBank's policies on how to handle the exact location for partial CDS's (`pyrodigal` might now output the start of the partial CDS at location 2 or 3, but I think GenBank requires it to be at 1), therefore this is still a draft PR. I will have time again in a few weeks to pick this up.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0454bfbd27e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.