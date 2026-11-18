# Issue

**Title:** Fix DAS_Tool bug

## Description

Update to **HiFi-MAG-Pipeline**:

Depending on version of DAS_Tool, the name of the helper script used to generate input files will change.

Digging in to the current script shows the prior name still listed, adding to confusion: https://github.com/cmks/DAS_Tool/blob/master/src/Fasta_to_Contig2Bin.sh

<= v1.1.3 : `Fasta_to_Scaffolds2Bin.sh`
> v1.1.3 : `Fasta_to_Contig2Bin.sh`

Snakemake was set to run with name from <= v1.1.3, causing errors if newer version was installed through conda.

This bug fix now pins the version of DAS_Tool to 1.1.6 and uses the `Fasta_to_Contig2Bin.sh` name in the workflow. This should eliminate errors stemming from incompatible version and script name.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93a7ff960b5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.