# Issue

**Title:** ignore seqs shorter than ksize in search

## Description

In the _Mus musculus_ refseq txome, there are some contigs <30bp in length, which break "search" with cdbg of ksize = 31. Here's a fix that ignores any contigs smaller than ksize.

Don't think this happens _too_ often. Here are the only two offending contigs in the refseq txome (GRCm38):
```
>NR_028434.1 Mus musculus snoRNA AF357359 (AF357359), small nucleolar RNA
ATCATGACGACAAATTTAATTCTGAGATCA

>NR_028557.1 Mus musculus small nucleolar RNA, C/D box 98 (Snord98), small nucleolar RNA
AATGCAGTGTGGAACATAATGAACTGAA
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34974a80d58d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.