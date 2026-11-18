# Issue

**Title:** Develop/trim overrepresented seq

## Description

Hi @ljmciver , 

I have added the "--run-trim-repetitve" flag parameter to trim the overrepresented sequences. Few of the major changes are listed below: 
- I am taking the min(length if overrepresented sequences) as we want to make it sensitive to trim all overrepresented sequences. I tested this with the MTX and MGX samples and works very well. 
- Since trimming the adapters contents is on by default using NEXTERA-PE, if "--run-trim-repetitve" is passed, then custom adapter.fa will be used which will have (all overrepresented sequences from FASTQC report+ sequencer source adapter content-NexteraPE-PE.fa adapters) trimming both adapters and overrepresented sequences.  

Can you take a look at the changes whenever you get the chance, please? 

Thanks,
Sagun

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5171e99570f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.