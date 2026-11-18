# Issue

**Title:** Integration of MMP Mar-databases in Kaiju (https://mmp.sfb.uit.no)

## Description

I not sure if this is of interest for the developers, but i have integrated the Marine Metagenomics Portal (MMP) Mar databases with Kaiju by modifying the makeDB script ++. 
The Mar databases (MarRef and MarDB) are marine manually curated reference databases for marine prokaryotic organisms. See https://mmp.sfb.uit.no for more information. The Mar databases will be extensively described in the Nucleic Acids Research databases issue 2018.

MMP now hosts static files for downloading and building these databases automatically, which are updated with each successive iteration of the Mar databases (https://s1.sfb.uit.no/)

Additional dependencies include Python2 and the HTSeq library for python (https://htseq.readthedocs.io)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0ff33f36550`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.