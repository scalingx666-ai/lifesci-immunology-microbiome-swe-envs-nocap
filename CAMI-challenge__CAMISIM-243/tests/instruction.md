# Issue

**Title:** Harden from_profile mode genome selection with new genomes, config loading, and output staging

## Description

This PR hardens the profile-driven metagenomic workflow around `get_genomes.py` and related Nextflow plumbing. The main goals are to support curated additional genomes with explicit quality gating, preserve the existing rank-first matching logic while adding source prioritization within a matched taxon, make profile-only community-design runs publish the expected core outputs, and fix several robustness issues observed in real runs.

Compared with `dev`, this branch changes the following files:

- `.gitignore`
- `convert_config.py`
- `nextflow.config`
- `pipelines/metagenomic/config/distribution.config`
- `pipelines/metagenomic/config/metagenomic.config`
- `pipelines/metagenomic/config/profile.config`
- `pipelines/metagenomic/from_profile.nf`
- `pipelines/metagenomic/metagenomic.nf`
- `pipelines/metagenomic/scripts/clean_up_sequences.py`
- `pipelines/metagenomic/scripts/get_genomes.py`
- `pipelines/shared/scripts/get_community_distribution.py`

## What changed

### 1. Make external config loading work reliably from outside the repo

File changed: `nextflow.config`

- Add `resolveExternalConfigPath(...)` and use it for `params.config`.
- Resolve config paths in this order:
  1. absolute path as provided
  2. relative to the launch directory
  3. relative to `projectDir` as a backward-compatible fallback
- Fail with a clear error if the external config file cannot be found in any of those locations.

Reason:
- Running `nextflow run ../pipeline/CAMISIM/main.nf --config ./some_config` from another working directory was brittle because config resolution depended on pipeline-relative paths.

### 2. Add profile-mode parameters for curated additional genomes and wire them through the workflow

Files changed:
- `convert_config.py`
- `pipelines/metagenomic/config/profile.config`
- `pipelines/metagenomic/from_profile.nf`

Changes:
- Add support for the following profile-mode parameters:
  - `prioritize_additional_genomes`
  - `additional_genomes_quality_file`
  - `additional_genomes_max_contamination`
  - `additional_genomes_min_completeness`
  - `additional_genomes_max_num_contigs`
- Update `convert_config.py` to emit these parameters and normalize boolean/string handling for them.
- Update `from_profile.nf` to provide explicit defaults for profile-only params when an external config does not import `profile.config`.
- Pass the new additional-genome selection and quality-threshold parameters into `get_genomes.py`.
- Guard `additional_references` access with `params.containsKey(...)` so profile runs do not crash when the parameter is absent.
- Extend `profile.config` comments to document accepted `additional_references` formats and the new quality-driven selection behavior.

Reason:
- The workflow previously assumed profile-specific params were always present, and it did not support quality-aware prioritization of additional genomes.

### 3. Preserve rank-first matching while adding source-aware genome selection

File changed: `pipelines/metagenomic/scripts/get_genomes.py`

Changes:
- Keep the existing taxonomy matching strategy: attempt the most specific resolved rank first, then move to broader ranks only if needed.
- Add source-aware candidate grouping within a matched taxon:
  - if `prioritize_additional_genomes = true`, draw from high-quality additional genomes first, then public reference genomes, then low-quality additional genomes as last resort
  - if `false`, draw from high-quality additional genomes and public references together, then use low-quality additional genomes only after the preferred pool is exhausted
- Apply the same candidate ordering in the `fill_up` fallback path.
- Require `additional_genomes_quality_file` when `additional_references` is set.
- Parse quality TSVs with required columns `genome_path`, `completeness`, `contamination`, and `num_contigs`.
- Mark additional genomes as quality-passing or low-quality based on configured thresholds.

Reason:
- This keeps taxonomic specificity as the primary priority while allowing curated genomes to be preferred within the same matched rank.

### 4. Make additional-genome and reference-genome table parsing more robust

File changed: `pipelines/metagenomic/scripts/get_genomes.py`

Changes:
- Add header-aware parsing for genome tables with alias support for common column names.
- Accept both 3-column and 4-column `additional_references` files:
  - `ncbi_taxid`, `scientific_name`, `genome_path`
  - `ncbi_taxid`, `scientific_name`, `genome_path`, `novelty_category`
- Default `novelty_category` to `known_strain` when omitted.
- Normalize genome-path keys when matching additional genomes to their quality TSV entries.

Reason:
- Real input files were failing on valid 3-column TSVs and on files with headers or alternative column names.

### 5. Fix taxonomy-name fallback and improve compatibility with installed ETE versions

File changed: `pipelines/metagenomic/scripts/get_genomes.py`

Changes:
- Fix the lineage-resolution fallback so that when exact NCBI name translation fails, the retry with the first token performs a real second translator lookup.
- Add a fallback import from `ete4` to `ete3` for `NCBITaxa`.

Reason:
- The previous retry branch reused stale lookup results and could silently drop recoverable ranks.
- Some environments had `ete3` available but not `ete4`, causing the profile workflow to fail before matching started.

### 6. Fix strain-count handling for profile mode

Files changed:
- `pipelines/metagenomic/scripts/get_genomes.py`
- `pipelines/metagenomic/config/metagenomic.config`

Changes:
- Validate `min_strains_per_otu` and `max_strains_per_otu` bounds explicitly.
- Add `draw_num_strains(...)` to handle edge cases cleanly.
- Preserve the previous geometric-style draw for larger ranges, but use a bounded uniform draw for small ranges where the old logic was pathological.
- Update config comments to reflect that `max_strains_per_otu = 1` is valid in profile mode.

Reason:
- The old draw logic behaved incorrectly for small ranges, especially `min=1, max=2`, and did not explicitly guard invalid bounds.

### 7. Publish the expected community-design outputs even when `just_community_design = true`

File changed: `pipelines/metagenomic/from_profile.nf`

Changes:
- Create `outdir/distributions/` during profile-mode genome selection.
- Copy `abundance_*.tsv` into `outdir/distributions/`.
- Copy `genome_to_id.tsv` into both:
  - `outdir/internal/genome_to_id.tsv`
  - `outdir/internal/genome_locations.tsv`

Reason:
- In profile mode, `just_community_design = true` stopped the workflow early before these files were published, which made the output layout incomplete for downstream reuse.

### 8. Prevent genome filename collisions when many input FASTAs share the same basename

Files changed:
- `pipelines/metagenomic/scripts/get_genomes.py`
- `pipelines/metagenomic/metagenomic.nf`
- `pipelines/metagenomic/scripts/clean_up_sequences.py`

Changes in `get_genomes.py`:
- Derive copied/downloaded genome filenames from the scientific label plus the source basename.
- Sanitize filenames and append numeric suffixes on collision.
- Preserve deterministic naming within a run.

Changes in `metagenomic.nf`:
- Pass full `[genome_id, path]` entries into `cleanup_and_filter_sequences` instead of flattening to basenames.
- Build an absolute temporary mapping file for cleanup rather than relying on staged filenames.

Changes in `clean_up_sequences.py`:
- Open genomes from their real full paths.
- Generate unique output names when different input genomes share the same basename, such as repeated `genomic.fna`.
- Write the remapped internal TSV against the renamed output files.

Reason:
- The workflow previously collided on shared basenames and could fail or mis-map genomes when multiple different source files had the same filename.

### 9. Improve `get_genomes.py` performance without changing the intended matching output

File changed: `pipelines/metagenomic/scripts/get_genomes.py`

Changes:
- Cache taxonomy name-to-taxid lookups.
- Cache taxid-to-rank lookups.
- Build reverse bucket indices so `no_replace` removal does not scan every rank/taxon bucket repeatedly.
- Stream writes to `genome_to_id.tsv`, `metadata.tsv`, and `abundance_*.tsv` instead of reopening files for every OTU.

Reason:
- `get_genomes.py` was noticeably slow on larger profiles, and the previous removal and file-writing paths had avoidable overhead.

### 10. Normalize boolean handling for community-distribution verbosity

Files changed:
- `pipelines/shared/scripts/get_community_distribution.py`
- `pipelines/metagenomic/config/distribution.config`

Changes:
- Accept case-insensitive boolean-like values for `verbose`, including `true/false`, `True/False`, `1/0`, and `yes/no`.
- Update the default config value from `"False"` to `false`.

Reason:
- The parser previously only accepted literal string values `True` and `False`, which was inconsistent with the rest of the Nextflow configs.

### 11. Ignore local run-specific config files in Git

File changed: `.gitignore`

Changes:
- Ignore:
  - `configs/`
  - `camisim.cfg`
  - `metax_bench_data.config`

Reason:
- These are local run/config artifacts that should not be picked up as repository changes.

### 12. Correct `*,cover` in `.gitignore`

File changed: `.gitignore`

Changes:
- From `*,cover` to `*.cover`

Reason:
- "," was a typo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6534d56ca4df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.