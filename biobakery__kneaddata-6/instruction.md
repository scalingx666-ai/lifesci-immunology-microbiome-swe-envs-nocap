# Issue

**Title:** New Adapter options

## Description

Hi @ljmciver , 

Below are the changes for this release: 
1. Removed the "overrepresented sequences" trimming till we figure out the threshold. 
2. Added the optional parameter "--sequencer-source" from which users can specify the sequencer source type. Based on the type, adapters provided by trimmomatic will be selected. 
These are the adapters that trimmomatic is providing with the license for distribution: 
[https://github.com/timflutre/trimmomatic/tree/master/adapters](https://github.com/timflutre/trimmomatic/tree/master/adapters)  

Curtis wants Nextera as the `default` for the sequencer-source. I did mention that trimmomatic is providing just one Nextera adapters for "Pair Ends" only. However, he suggested using the same for the Single End as well. 

Please let me know if anything needs to be changed and I can update the README accordingly after the merge. I'll ping you on slack tomorrow as it is already after-hours today.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `22027a00c592`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.