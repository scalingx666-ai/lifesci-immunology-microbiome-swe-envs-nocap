# Issue

**Title:** Feature/improve antismash processing

## Description

- Replaced the script that generates a GFF file from the antiSMASH results with the [mgnify-pipelines-toolkit](https://github.com/EBI-Metagenomics/mgnify-pipelines-toolkit ) script from to include full information about the BGCs
- Split the antiSMASH module into a separate antiSMASH run module and a GFF building module
- Added an extra field (`antismash_product`) into the final genome GFF file

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a7c169d1f6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.