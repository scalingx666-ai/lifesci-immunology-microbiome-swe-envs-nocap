# Issue

**Title:** follow the paired reads name convention, /1 and /2 at the end

## Description

I have use [ncbi-genome-download](https://github.com/kblin/ncbi-genome-download) to download some bacteria reference genome,
and merge them to one single file, then use [InSilicoSeq](https://github.com/HadrienG/InSilicoSeq) to generate metagenomics reads.
But when I use bwa mapping these reads to assembly genome, bwa told me, 
**paired reads have different name**.
So, I change the code. May be helpful.
Thank HadrienG!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3e711373cbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.