# Issue

**Title:** Assembly

## Description

I'm sorry there where still some bugs in #40 I corrected them here and tested them on paired and single end dummy data. I pushed them directly to the master to resolve the bugs. 

Now we have:

 -trimming
 - decontamination
 - deduplication (optional)

QC reads:

preprocessing assembly:
 - normalization
 - errorcorr
 - merging

order can be changed via the list in the config file.

However the QC reads are maped to the contigs, which alow also vairant calling. 

@brwnj  what do you think of that?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efd96cb94ee3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.