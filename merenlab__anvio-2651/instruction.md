# Issue

**Title:** Trnahits bug: CCT_Arg vs Arg_CCT naming mismatch

## Description

For issue #2650,   I verified this in the generated test DB: hmm_hits_info for Transfer_RNAs contains CCT_Arg, while hmm_hits contains Arg_CCT using the latest commit to the master branch `a4204c5697ed5aba79a17d2c3ad3d95666052e86`. 

I believe the right fix is to make the metadata use the same naming convention as the hit rows by switching `possible_genes.append(f'{acdn}_{decoded_aa_type}')` to `possible_genes.append(f'{decoded_aa_type}_{acdn}')` in the `trnahits.py` file.

This was accomplished by two small changes:
-  Transfer_RNAs metadata now registers possible genes as decoded_AA_type_anticodon, e.g. Arg_CCT, matching the actual `hmm_hits.gene_name values`.
- Added a local consistency check before writing tRNA hits into the HMM tables. If future naming logic drifts again, it raises a ConfigError at write time instead of producing a bad DB that crashes later in `anvi-display-contigs-stats`.

People would beed to regenerate their contig.db later on if they wanted this case to be fixed. 

The workflow with running the command `anvi-self-test --suite workflow-contigs -T 40 --output-dir test_output` in the `test` directory in anvi'o now runs to completion; however, due to running it on a remote server without x11 / port forwarding enabled **I was unable to see/test the anvi-display-contigs-stats to verify the visuals weren't odd**.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be6c395e8b7f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.