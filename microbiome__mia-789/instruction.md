# Issue

**Title:** Add Joint-RPCA to mia: methods, tests, examples, vignette

## Description

### Summary
This PR adds a complete Joint-RPCA (OptSpace) module for multi-omic integration in `mia`.
It introduces the full backend implementation, preprocessing utilities, and example workflows for replicating iHMP/IBDMDB analyses.

The update includes:
- Core functions (`jointRPCA`, `jointRPCAuniversal`, and supporting OptSpace solvers) for single- and multi-omic RPCA ordination.
- Comprehensive preprocessing, projection, and masking utilities ensuring stable compositional handling.
- Unit tests validating structure, reproducibility, and projection consistency on synthetic data.
- Quarto example notebooks demonstrating two- and three-omic IBDMDB analyses, benchmarking, and replication of published results.
- Example IBDMDB data subsets for reproducible testing (with instructions for optional MTX data download).

Together, these additions enable full Joint-RPCA analysis and validation within R, reproducing the same behavior as the original Python implementation on IBD multi-omic datasets.

### What's included
#### Core Joint-RPCA Implementation
- `R/jointRPCA.R` — Implements the core Joint Robust Principal Component Analysis (Joint-RPCA) using the OptSpace algorithm across one or more compositional tables. Handles preprocessing, filtering, shared sample alignment, and factorization for multi-omic inputs.
- `R/jointRPCAuniversal.R` — Provides a universal user-facing wrapper for `jointRPCA()`, automatically detecting input type (`matrix`, `list`, `SummarizedExperiment`, or `MultiAssayExperiment`) and dispatching accordingly.
- `R/jointRPCAutils.R` — Utility functions supporting the main pipeline, including data validation, helper wrappers, and structure checks used throughout the Joint-RPCA modules.
#### OptSpace Optimization Backend
- `R/jointOptspaceHelper.R` — Internal engine that orchestrates the Joint OptSpace factorization: splitting data into train/test subsets, calling the solver, constructing ordination results, and projecting held-out samples.
- `R/jointOptspaceSolve.R` — Low-level OptSpace solver implementation for joint factorization across multiple paired matrices, producing shared sample embeddings and per-view feature loadings.
- `R/optspaceHelper.R` — Helper for single-view (non-joint) OptSpace-based RPCA. Used for initialization and simple validation steps when only one table is provided.
#### Preprocessing and Data Handling
- `R/rpcaTableProcessing.R` — Handles filtering, normalization, and zero-count removal for compositional tables prior to RPCA. Ensures numeric stability and removes low-prevalence or low-abundance features/samples.
- `R/maskValueOnly.R` — Safely converts numeric inputs into masked matrices by replacing non-finite values with `NA` while preserving dimensionality and a logical mask for missing positions.
- `R/transform.R` — Implements `.transform()`, an internal projection function for aligning new compositional data (matrices or per-view lists) to an existing Joint-RPCA ordination space.
- `R/transformHelper.R` — Supports `.transform()` with `.transform_helper()`, handling both single-view and multi-view projections, optional sample deduplication, and alignment to training feature sets.
#### Testing
- `tests/testthat/test-jointRPCA.R` — Synthetic unit tests verifying output structure, behavior, and robustness of `jointRPCA()` and `.transform()` across single- and multi-omic data.
Covers shared-sample alignment, projection correctness, duplicate-ID errors, and consistency of component dimensions.
#### Reproducible Examples and Benchmarks
Located under `inst/examples/`, these Quarto notebooks demonstrate reproducible analysis pipelines and validation of the Joint-RPCA implementation.
- `inst/examples/joint_rpca_example.qmd` — Minimal working example showing how to run Joint-RPCA on synthetic data and inspect ordination results.
- `inst/examples/ihmp_ibd_replication.qmd` — Replication of the iHMP IBD dataset single-omic (16S) analysis to validate consistency with published Python-based results.
- `inst/examples/ibdmdb_2omic_jointrpca.qmd` — Two-omic (MGX + MTX) Joint-RPCA integration on the IBDMDB dataset, demonstrating successful cross-omic ordination.
- `inst/examples/ibdmdb_3omic_jointrpca.qmd` — Three-omic (16S + MGX + MTX) integration example; demonstrates full pipeline behavior and visualization when shared samples are limited.
- `inst/examples/ibdmdb_benchmarking.qmd` — Performance benchmarking and variance-explained analysis comparing different omic combinations to assess numerical stability and efficiency of the R implementation.
#### Example Data (IBDMDB)
Stored under `inst/examples/data_ibdmdb_raw/` — small real-world data subset for demonstration and testing.
- `taxonomic_profiles_mtx_new.tsv` — Metatranscriptomic taxonomic profiles (subset of HMP2 IBDMDB).
- `taxonomic_profiles_mgx_new.tsv`, `taxonomic_profiles_mgx.tsv` — Metagenomic taxonomic profiles.
- `taxonomic_profiles_16s_new.tsv`, `taxonomic_profiles_16s.tsv` — 16S rRNA sequencing taxonomic profiles.
- `hmp2_metadata_2018-08-20.csv` — Subject-level and sample-level metadata, including diagnosis and visit information.

**Note:** The metatranscriptomic functional table `ecs_relab.tsv` (taxonomic profiles for MTX from HMP2) is not included due to size limits.
To reproduce full analyses, download it manually from the official iHMP IBDMDB data portal and place it in the same folder (`inst/examples/data_ibdmdb_raw/`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a18e5d89d57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.