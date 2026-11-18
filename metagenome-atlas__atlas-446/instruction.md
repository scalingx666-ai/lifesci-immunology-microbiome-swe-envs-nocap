# Issue

**Title:** vamb params & vamb v3.0.3

## Description

Hi @SilasK 

1. I tried the new version, but still couldn't make vamb work using your dependency setting. I'm not sure if you have recently
used it to rebuild a conda environment. At least, it didn't work for me. 
As Jakob has released new `vamb v3.0.3`, it may be a better idea to use this.

2. the `vamb` params is a bit wired.
`-m` indicates min-length contigs for binning
`-minfasta` indicates min bin size to keep. You can find the description here https://github.com/RasmussenLab/vamb/tree/master/workflow

I chose your default values to keep bins > 2MB, which shall be comparable to the bins from `metabat`. Previously you chose `-minfasta 2000`, you will have too many bins belonging to phage and plasmid....

I have tested it and it worked for my data. You can find the details in the PR.

I will test `semibin` and give you updates later.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07118cd299a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.