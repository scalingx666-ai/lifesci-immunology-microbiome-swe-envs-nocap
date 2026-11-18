# Issue

**Title:** Fix statistical validity and data alignment issues across analyses

## Description

## Summary
This PR addresses multiple statistical validity and data handling issues across the microbiome analysis pipeline, including PERMANOVA exchangeability violations, missing data handling, incorrect degrees of freedom calculations, and data alignment problems.

## Key Changes

### PERMANOVA and Beta Diversity Analysis
- **generate_beta_test_single.R**: Added warning when `time.var` has multiple levels but `t.level` is NULL, as pooling timepoints violates PERMANOVA's exchangeability assumption and inflates Type-I error
- Implemented explicit complete-case filtering for both metadata and distance matrices before PERMANOVA, ensuring correct sample-to-row pairing regardless of input order or whether distances are provided or computed
- Removed premature distance subsetting that could cause misalignment

### Alpha Diversity Analysis
- **generate_alpha_volatility_test_long.R**: Added guard against missing covariate values that would cause `model.matrix()` to silently drop rows and misalign residuals
- **generate_alpha_per_time_test_long.R**: Fixed group reference level pinning within timepoint subsets to prevent mislabeling when a timepoint lacks the global reference group
- **mStat_calculate_alpha_diversity.R**: Added validation that Chao1 and ACE estimators receive integer count data, as they are undefined for normalized/relative-abundance data

### Taxa Change Analysis
- **generate_taxa_change_test_pair.R**: Fixed winsorization to operate per-taxon (across samples) rather than per-sample (across taxa), matching the per-taxon pseudocount convention
- Corrected complete-case filtering logic to properly identify subjects with complete change scores across all taxa

### Adjusted Distance Calculation
- **mStat_calculate_adjusted_distance.R**: Removed incorrect re-weighting by eigenvalues that was squaring the axis scaling, as `cmdscale()` already returns properly scaled coordinates

### Linear Model Analysis
- **generate_taxa_test_single.R**: Fixed residual degrees of freedom calculation to account for actual design matrix rank rather than variable count, which was overstating df for multi-level factors
- **generate_beta_volatility_test_long.R** and **generate_taxa_volatility_test_long.R**: Reordered formula terms to place `group.var` last, ensuring sequential (Type-I) ANOVA F-tests equal the covariate-adjusted omnibus test

### Data Normalization and Conversion
- **mStat_normalize_data.R**: Added `seed` parameter (default 123) to make rarefaction reproducible while preserving caller's RNG state
- **mStat_convert_phyloseq_to_data_obj.R**: Added `drop = FALSE` to preserve matrix structure when subsetting single rows; added `check.names = FALSE` to preserve metadata column names

### Statistical Testing Functions
- **linda.R** and **linda2.R**: Fixed winsorization to only execute when `outlier.pct` is not NULL, preventing unintended behavior when `is.winsor = TRUE` but `outlier.pct = NULL`; updated documentation to clarify default behavior

## Notable Implementation Details
- Complete-case filtering now consistently applied across all analysis types to prevent silent data misalignment
- Explicit validation of data assumptions (integer counts for richness estimators, no missing covariates) with informative error messages
- Careful preservation of matrix/data.frame structure and column names during subsetting operations
- Proper handling of random seed management to ensure reproducibility without affecting caller's RNG state

https://claude.ai/code/session_01CDuBVvoJeszwbQGtXC7uFa

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6109b493bf34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.