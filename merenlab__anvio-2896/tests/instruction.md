# Issue

**Title:** Classify I34 tRNA-seq seeds in `anvi-run-trna-taxonomy`

## Description

`anvi-run-trna-taxonomy` searches each tRNA against the GTDB genes of its labeled anticodon. tRNA-seq seeds are labeled with the anticodon that is read from transcripts, but reverse transcription reads inosine, a modified A, as G. Seeds of tRNA-Arg-ACG and tRNA-Leu-AAG, the two bacterial tRNAs known to have I34 in various clades, therefore can be labeled GCG and GAG, which resulted in searches against GCG and GAG genes rather than the correct ACG and AAG genes. As a result, none of the 34 Arg_GCG seeds in the tRNA-seq test data were classified.

## Fix

- In tRNA-seq contigs databases (`db_variant` 'trnaseq'), seeds labeled GCG and GAG are also searched against ACG and AAG genes.
- Each seed keeps the hits of the GCG vs. ACG or GAG vs. AAG genes whose best alignment has the higher bitscore, and the consensus is computed from the top hits to the chosen database, as before. Bit score is used rather than percent identity because a short partial alignment can reach a higher identity than a full-length one.
- `trna_taxonomy` still stores the labeled anticodon rather than that of the gene. `anvi-estimate-trna-taxonomy` is unaffected by the fix.
- The run's summary table gets an `as_I34` column, and `--all-hits-output-file` gets a `searched_anticodon` column. These are described in the program docs.
- Contigs databases that aren't the `trnaseq` variant are not affected by the fix.
- Changes were checked with the current GTDB r89 data and with the updated GTDB v226 data of #2492. In the self-test, 31 of 34 Arg_GCG seeds and 5 more Leu_GAG seeds are now classified. The three Arg_GCG seeds left unclassified are 46-49-nt fragments: two are interior pieces of tRNA-Leu and tRNA-Ser that anvi-trnaseq labeled Arg_GCG 3' fragments, and one is from tRNA-Arg but has no close GTDB relative.
- I34 seeds were simulated by changing A34 to G34 in ACG and AAG genes, and genuine GCG and GAG genes served as controls. With the source genome in GTDB, the right genes were chosen for the 300 genes per group, and no genuine G34 gene changed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56e8f2681e57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.