# Issue

**Title:** Performance improvements of SPLIT_PROTEINS module

## Description

Rewrite script for SPLIT_PROTEINS module to remove nested for loop. 
Also some refactoring done to improve readability and clarity
Running time went down from 43 hours on big assembly from ASG dataset to 5 mins. 

### Purpose of this script

This script takes:
- a FASTA file with selected subset contigs, and
- a FASTA file with all predicted proteins,

and creates a new proteins FASTA that contains only proteins that belong to those selected contigs.

#### How it works:

1. Read contigs and all proteins from FASTA files.
2. Build a lookup table from contig id to its protein records.
3. For each selected contig:
- find proteins that match its contig id,
- if contig is marked as prophage, keep only proteins that overlap the prophage region (or keep all for circular phages),
- update headers for proteins from contigs marked as prophage so they match prophage contig naming.
4. Write matched proteins to the output FASTA.
5. Validate results:
- fail if no proteins were written,
- fail if the same protein would be written more than once.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ec5159133d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.