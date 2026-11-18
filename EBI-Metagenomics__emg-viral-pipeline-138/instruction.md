# Issue

**Title:** Add annotations for momofy

## Description

Added `viral genes` and `kmer frequency` to checkV results attributes to final GFF. Also added `virify_quality` {HC, LC, PP, unknown} for all annotations right after ID. _If quality is unknown - it seems an error in parsing. Better to report it to me to fix_

example:
```
NODE_5186_length_8751_cov_4.185028   VIRify viral_sequence 1    8751  .    .    .    ID=NODE_5186_length_8751_cov_4.185028|viral_sequence;virify_quality=LC;gbkey=mobile_element;mobile_element_type=phage_linear;checkv_provirus=No;checkv_quality=Low-quality;miuvig_quality=Genome-fragment;kmer_freq=1;viral_genes=15;taxonomy=Fletchervirus%3BEucampyvirinae
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa59e729331e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.