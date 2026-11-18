# Issue

**Title:** Changes/trim off default

## Description

Hi @ljmciver , 

This a new pull request for turning off `trim-repetitive` and adding `--run-trim-repetitive` to trim the overrepresented sequences using FASTQC reports. 

I tested these changes with Amplicon (16S) and Shotgun(MGX and MTX). I confirm that the depletion of reads is only seen in the 16s Amplicon sequencing. Since we have turned the option off by default and as we are recommending this option only for Shotgun sequences, I have not included any threshold option for the MGX and MTX output sequence since they are performing great without any thresholds (with only 10%-20% of the initial read count removal ).   

Please let me know if any changes are needed.

Many Thanks,
Sagun

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a36a8029d467`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.