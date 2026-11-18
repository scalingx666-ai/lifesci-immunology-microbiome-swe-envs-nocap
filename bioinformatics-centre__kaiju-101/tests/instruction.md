# Issue

**Title:** Mar databases V3 update

## Description

The Mar databases from The Marine Metagenomics Portal (https://mmp.sfb.uit.no/) are now in their third iteration, and I have added some minor codes snippets to account for this.

Version 3 includes over 9000 marine species and the ability to distinguish between reference organisms (MarRef), complete organisms (MarDB) and Metagenomic Assembled Genomes (MarDB MAGS) as defined at the portal.
The makeDB.sh flag -m will download and build the complete database, but for special cases, it is possible to build subsets pertaining to discrete divisions, f.ex only reference sequences (MarRef), by simply commenting out a line or two in the makeDB.sh script. I did not add flags for this, as I do not want to overpopulate the makeDB.sh help text with too much Mar related information. 

Version 2, which is the current integrated DB version in Kaiju atm., will still be supported until this pull request is accepted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `964d5b832f4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.