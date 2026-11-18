# Issue

**Title:** feat: add ITSxRust as alternative ITS extractor

## Description

## Description

Addresses #956

Adds [ITSxRust](https://github.com/ayobi/ITSxRust) as an optional alternative to ITSx for ITS region extraction, selectable via `--its_extractor itsxrust` (default remains `itsx` for backward compatibility).

## Changes

- **New module:** `modules/local/itsxrust_cutasv.nf` — mirrors the ITSX_CUTASV interface (same inputs/outputs) so downstream processes (FILTER_LEN_ITSX, taxonomy, summary report) work unchanged
- **Workflow:** `workflows/ampliseq.nf` — conditional branching between ITSX_CUTASV and ITSXRUST_CUTASV based on `params.its_extractor`
- **Config:** `conf/modules.config` — ITSXRUST_CUTASV block with automatic preset selection (ONT default, HiFi when `--pacbio` is set)
- **Params:** `nextflow.config` + `nextflow_schema.json` — new `its_extractor` parameter (enum: `itsx`, `itsxrust`)
- **Docs:** `docs/usage.md` (new ITS extraction tool subsection), `docs/output.md` (updated ITSx section to cover both tools)
- **Meta:** `CHANGELOG.md`, `CITATIONS.md`

## Implementation notes

- The HMM profile (`F.hmm`) is bundled in both the Docker image and Bioconda package at `/usr/local/share/itsxrust/hmm/F.hmm` — no user-supplied file needed
- ITSxRust output filenames are renamed to match ITSx conventions (uppercase ITS1/ITS2) for seamless downstream compatibility
- QC JSON is converted to an ITSx-compatible `summary.txt` format for the summary report

## Testing

- `nextflow run . -profile test_pacbio_its,docker --outdir test_itsx` — **passes** (ITSx path unchanged)
- `nextflow run . -profile test_pacbio_its,docker --its_extractor itsxrust --outdir test_itsxrust` — ITSXRUST_CUTASV completes successfully ✔, output feeds into FILTER_LEN_ITSX correctly. Note: a pre-existing YAML parsing error in `utils_nfcore_pipeline` on the dev branch causes the run to fail late in the pipeline; this is unrelated to this PR.

## Dependencies

- Docker image available now: `ghcr.io/ayobi/itsxrust:0.2.2`
- Users running with `-profile docker` or `-profile singularity` can use this immediately; conda users will need the Bioconda PR to merge first

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f388639ffa99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.