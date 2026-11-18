# Issue

**Title:** Provide Precomputed Protein Sequences

## Description

This PR adds the ability to provide precomputed protein sequences as input, eliminating the need for Binette to perform gene prediction. This feature addresses the request in issue #30.  

### Usage  
A new argument, `--proteins`, has been introduced. This should point to a FASTA file containing all predicted proteins for the assembly.  

### Requirements  
The provided protein sequences must follow Pyrodigal’s naming convention: `<contigID>_<GeneID>`.  
- `<contigID>`: The name of the contig.
- `<GeneID>`: An integer identifying the gene.  

If a contig extracted from the protein file is not present in the provided contig file, the program will raise an error to ensure consistency between inputs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44a4baceaf10`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.