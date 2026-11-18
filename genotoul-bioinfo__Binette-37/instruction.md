# Issue

**Title:** Fix wrong input proteins management

## Description

This PR resolves the issue described in #35, related to how Binette handles proteins given as inputs.

Currently, Binette excludes unbinned contigs to avoid unnecessary computations (e.g., running Prodigal and Diamond on unused contigs). While this saves time, it creates a mismatch when protein files are provided, as unbinned contigs are still present in the protein data. This inconsistency triggers errors during the step that checks for differences between the assembly contigs and the proteins.  

### Solution  

**Filtered Protein File**  
   - The input protein file is now filtered to exclude genes from unbinned contigs.  
   - A filtered version of the file is saved in `<outdir>/temporary_files/` and passed to Diamond for gene annotation.  
   - This ensures only genes from contigs of interest are annotated, resolving the mismatch.  


#### Additional changes 

 **Temporary File Compression**  
   - Temporary files in `<outdir>/temporary_files/`, including the FAA file and Diamond results, are now compressed to save disk space.  
   - The pyfastx index for the contig file is now stored in <outdir>/temporary_files/ instead of alongside the assembly file. This ensures files are written only to the intended directory, avoiding unwanted file placements.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `570150616177`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.