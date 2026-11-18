# Issue

**Title:** UCHIME2 and 3

## Description

Dear all,
I added the UCHIME 2 and 3 commands ([paper](https://www.biorxiv.org/content/early/2016/09/09/074252)) into VSEARCH (`--uchime2_denovo` and `--uchime3_denovo`). These algorithms are well suited for detecting chimeras from denoised sequences. The implementation is simple: if a perfect model is found (dQM=0 and dQT>0), the read is classified as chimeric. Moreover, unoise3 removes chimeras using exactly the same algorithm as uchime3_denovo (related to #283). The uchime2 and 3 commands differ only in the default value of `--abskew` (2.0 for uchime2 and 16.0 for uchime3, see [here](https://www.drive5.com/usearch/manual/cmd_uchime3_denovo.html)).

I compared the implementation with USEARCH obtaining similar but not identical results. It seems that sometimes VSEARCH find different parents that are unable to build a perfect model. Any suggestion?

## Results UCHIME2
```sh
vsearch --uchime2_denovo denoised.fa --chimeras vsearch_chim.fa
usearch9 -uchime2_denovo denoised.fa -chimeras usearch_chim.fa
```

### Minimal-paired
VSEARCH chimeras: 0
USEARCH chimeras: 0
chimeras in VSEARCH but not in USEARCH: 0
chimeras in USEARCH but not in VSEARCH: 0
### MiSeq 16S
VSEARCH chimeras: 236
USEARCH chimeras: 306
chimeras in VSEARCH but not in USEARCH: 0
chimeras in USEARCH but not in VSEARCH: 70
### MiSeq ITS
VSEARCH chimeras: 4
USEARCH chimeras: 4
chimeras in VSEARCH but not in USEARCH: 1
chimeras in USEARCH but not in VSEARCH: 1

## Results UCHIME3
```sh
vsearch --uchime3_denovo denoised.fa --chimeras vsearch_chim.fa
usearch9 -uchime2_denovo denoised.fa -chimeras usearch_chim.fa -abskew 16
```

### Minimal-paired
VSEARCH chimeras: 0
USEARCH chimeras: 0
chimeras in VSEARCH but not in USEARCH: 0
chimeras in USEARCH but not in VSEARCH: 0
### MiSeq 16S
VSEARCH chimeras: 107
USEARCH chimeras: 115
chimeras in VSEARCH but not in USEARCH: 0
chimeras in USEARCH but not in VSEARCH: 8
### MiSeq ITS
VSEARCH chimeras: 4
USEARCH chimeras: 3
chimeras in VSEARCH but not in USEARCH: 1
chimeras in USEARCH but not in VSEARCH: 0

Moreover, it should fix #288.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90caad325649`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.