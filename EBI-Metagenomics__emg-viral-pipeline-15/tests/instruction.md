# Issue

**Title:** 10% first threshold and modified proportion per rank

## Description

@guille0387 implemented discussed changes of the voting system to better reflect the updated NCBI taxonomy metadata file and general taxonomic assignments:

* lowered the 20% cutoff of discovered informative HMMs to 10%
* taxonomy is now assigned by comparing the number of HMMs from the same rank to the total number of identified models for this rank {genus/subfamily/family/order} 
    * for example: before the number of HMMs identified for a specific genus were compared to the total number of __all__ identified proteins and due to that the cutoff of 60% was not reached in many cases

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74810a691a8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.