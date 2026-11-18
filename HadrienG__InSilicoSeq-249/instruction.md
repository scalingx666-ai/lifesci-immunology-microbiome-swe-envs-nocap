# Issue

**Title:** New MiSeq and NextSeq error models

## Description

Hi Hadrien,

I have added the new MiSeq and NextSeq models to the profiles-folder and made them available through the cli. Both the MiSeq and NextSeq error models produce paired-end reads of 301bp. The miSeq models are based on the reads of the 8 runs of SRA project [ERP022313](https://trace.ncbi.nlm.nih.gov/Traces/study/?acc=ERP022313&o=acc_s%3Aa).
 
- miSeq_0.npz --> filter: none
- miSeq_20.npz --> filter: the forward and reverse read have a mean quality score >= 20 
- miSeq_24.npz --> filter: the forward and reverse read have a mean quality score >= 24
- miSeq_28.npz --> filter: the forward and reverse read have a mean quality score >= 28
- miSeq_32.npz --> filter: the forward and reverse read have a mean quality score >= 32
- miSeq_36.npz --> filter: the forward and reverse read have a mean quality score >= 36
- nextSeq.npz --> filter: none

Below are the placeholder-names that I have used for the error models in the cli. I am not very happy with the current names: it's not clear what the number means. At the same time I don't want to use very long and extensive names. The naming of the error models is open for discussion. 
 
- miSeq_0.npz --> "miseq"
- miSeq_20.npz --> "miseq-20"
- miSeq_24.npz --> "miseq-24"
- miSeq_28.npz --> "miseq-28"
- miSeq_32.npz --> "miseq-32"
- miSeq_36.npz --> "miseq-36"
- nextSeq.npz --> "nextseq"

Let me know what you think of it.

Best,
Stefan

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb425d15387b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.