# Issue

**Title:** resolve the hang problem #226

## Description

Replacing multiprocessing with concurrent.futures to resolve the hang
Preloading output_tab_sequences into dictionary to improve program efficiency

Testing with SRA fastq: [DRR387644](https://www.ncbi.nlm.nih.gov/sra?LinkName=biosample_sra&from_uid=34367085)
It's illummia 150bp paired-end reads from Klebsiella pneumoniae
File size is 541M.
```
fasterq-dump -O fq DRR387644
time rgi bwt -1 fq/DRR387644_1.fastq -2 fq/DRR387644_2.fastq -a kma -o bwt_out --include_wildcard --include_other_models
real    4m33.099s
user    6m31.818s
sys     0m50.640s
```
It took about 4.5 minutes to finish.
The current codes () spent more than 1 hr, so I didn't wait it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `778b83d232f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.