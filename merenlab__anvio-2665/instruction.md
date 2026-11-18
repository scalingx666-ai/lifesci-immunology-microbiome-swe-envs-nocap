# Issue

**Title:** added anvi-script-kofam-accessions-to-hmms-directory

## Description

# Summary
This PR introduces a new script, `anvi-script-kofam-accessions-to-hmms-directory`, which allows users to extract a specific subset of KOfam HMM models from their local `anvi’o` KEGG setup into a standalone, `anvi’o`-compatible HMM directory, similarly to `anvi-script-pfam-accessions-to-hmms-directory`.  

While `anvi-run-kegg-kofams` is the "gold" standard for comprehensive KEGG profiling, users often need to focus on specific pathways or a handful of KOs across massive datasets, e.g. for a quick identification of potential populations of interest when binning the MAGs in `anvi-interactive`. Running the entire KOfam in such cases is computationally expensive, so this script bridges this gap by enabling the use of `anvi-run-hmms` with a targeted subset of KOfam models.

# Key features
   * Selective extraction: extracts HMMs using `hmmfetch` based on a list of KOs of interest.
   * Automatic HMM patching: KOfam models extracted via `hmmfetch` often lack critical metadata. The script automatically patches resulting HMMs with:
       * ACC lines (accession IDs) to ensure compatibility with anvi-run-hmms;
       * DESC lines (function definitions) for better downstream reporting;
       * GA lines (gathering thresholds) derived from the KEGG ko_list, allowing the use of the `--cut_ga` flag in `anvi-run-hmms`;
   * Stray KO support: includes a `--include-nt-KOs` flag to toggle the inclusion of models that do not have KEGG-defined bitscore thresholds, mirroring the behavior of `anvi-run-kegg-kofams`.

# Usage example

```bash
# extract KOs of interest
anvi-script-kofam-accessions-to-hmms-directory \
    --kofam-accessions-file my_favorite_kos.txt \
    -O MY_HMMS

# run profiling
anvi-run-hmms \
    -c CONTIGS.db \
    --hmm-profile-dir MY_HMMS \
    --add-to-functions-table
```

# Technical note on result discrepancies

During testing, I compared the results of this script + `anvi-run-hmms` against the full `anvi-run-kegg-kofams` run using the file in `anvio/tests/sandbox/data/metagenomes/human_gut/IGD_SUBSET/CONTIGS.db`. Users should be aware that:

1. Strict filtering: because `anvi-run-hmms` is strictly bitscore-based, it may report fewer hits (~10-12% less in the IGD subset test) compared to `anvi-run-kegg-kofams`, which utilizes a fallback e-value heuristic to recover hits that barely miss the bitscore threshold.
2. Database size effect: searching against a smaller subset of HMMs can lead to e-value inflation, where weak hits become statistically significant due to the reduced search space. 

# And now for something completely different...

This could be implemented in a different way by allowing the user to specify a subset of KOfam models to be downloaded with `anvi-setup-kegg-data` instead of the full set. This would then allow the user to run `anvi-run-kegg-kofams` on this reduced dataset and take advantage of the improved heuristics implemented there. But I'm tired now, and even with the help of Gemini, this took way longer than what I expected. So I let the `anvi'o` experts decide if this is useful or not :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35e961dbbc07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.