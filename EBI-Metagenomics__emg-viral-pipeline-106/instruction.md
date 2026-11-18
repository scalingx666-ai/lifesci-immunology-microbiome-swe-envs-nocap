# Issue

**Title:** Metadata file v4, also included a warning about the deleted taxa.

## Description

The warning message looks like:
```
nextflow run virify.nf --meta_version v4 --fasta nextflow/test/assembly.fasta
N E X T F L O W  ~  version 23.04.0
Launching `virify.nf` [sharp_carlsson] DSL2 - revision: 690a9ff68f

Profile: standard

Current User: mbc
Nextflow-version: 23.04.0
Starting time: 01-04-2023 21:09 UTC
Workdir location:
  /home/mbc/projects/emg-viral-pipeline/work
Databases location:
  nextflow-autodownload-databases

CPUs to use: 2
Output dir name: results

Dev ViPhOG database: v3
Dev Meta database: v4

Only run annotation: false

Warning: --meta_version v4 does not include the following discontinued virus taxa
(according to ICTV) anymore and they have been excluded from the dataset.

Siphoviridae
Podoviridae
Myoviridae
Caudovirales
Allolevivirus
Autographivirinae
Buttersvirus
Chungbukvirus
Incheonvirus
Leviviridae
Levivirus
Mandarivirus
Pbi1virus
Phicbkvirus
Radnorvirus
Sitaravirus
Vidavervirus

executor >  local (6)
...
```

This one should fix #104

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a906e363e7ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.