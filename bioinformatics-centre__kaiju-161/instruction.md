# Issue

**Title:** use wget ftp globbing

## Description

Use wget ftp globbing capabilities instead of probing for future files 

some files from refseq section are missing dur to manual listing
eg: plasmid.N.genomic.gbff.gz, with N currently ranging from 1 to 7, but 8 is already here.
instead of hard-coding required files use ftp globbing to get what's available

same apply for viral.N.genomic.gbff.gz when viral.3.genomic.gbff.gz will be available it will be grabbed. 

NB I  must admit that I'm pretty reluctant to have something like 
`command that potentialy will fail || true`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33bca1314d71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.