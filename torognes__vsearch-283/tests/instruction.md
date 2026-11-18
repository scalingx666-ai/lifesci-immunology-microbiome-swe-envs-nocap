# Issue

**Title:** UNOISE

## Description

Dear All,
I just implemented the UNOISE algorithm (https://www.biorxiv.org/content/early/2016/10/15/081257.full.pdf+html) into VSEARCH. 

The command is quite similar to the one implemented in USEARCH (https://drive5.com/usearch/manual/cmd_unoise3.html) with the options `--minsize` and `--unoise_alpha`. All the options available for the clustering algorithms (with the exception of the global clustering threshold (`--id`) and the pairwise identity definition (`--iddef`)) remain valid.

This implementation does not include the chimera detection whereas the original does. Therefore, the additional chimera removal step is necessary. The abundance skew parameter is set to 16 in UCHIME3/UNOISE3 (USEARCH v10). So, the original command:
```bash
usearch -unoise3 uniques.fa -zotus zotus.fa
```
will be:
```bash
vsearch --unoise uniques.fa --sizein --sizeout --centroids zotus_chim.fa 
vsearch --sortbysize zotus_chim.fa --output zotus_sorted.fa
vsearch --uchime_denovo zotus_sorted.fa --abskew 16 --nonchimeras zotus.fa
```
I tested the implementation on the `Minimal-paired`, `MiSeq 2x250 16S V4` and `MiSeq 2x300 ITS` datasets (available at https://www.drive5.com/usearch/manual/pipe_examples.html) obtaining near identical results. Small differences are generated in the chimera filtering step, probably due to small deviations in the implementation.

I didn't update the man file but I'm happy to update it if you consider this pull request.
Comments are welcome,

Davide

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `608b23751f79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.