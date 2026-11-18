# Issue

**Title:** Use aligned FASTA for KEGG HMM construction

## Description

## Summary

This PR updates KEGG/KOfam HMM construction to pass aligned FASTA (`afa`) into `hmmbuild` instead of requesting CLUSTAL-like output from the MUSCLE driver.  

CLUSTAL-like output is no longer supported by MUSCLE v5. To generate such output, conversion code will need to be added. Currently, the only place that clustalw_format output is used is by `hmmbuild`. The MUSCLE driver already returns aligned FASTA by default, and `hmmbuild` accepts this via `--informat afa`, so this removes the only in-repo need for MUSCLE's CLUSTAL output mode while preserving the resulting HMM behavior.


A follow up PR looks at updating the MUSCLE dependency or driver CLI handling.

## Testing

- Compared the old MUSCLE 3 `clustalw_format=True` + `hmmbuild --informat clustallike` path against the new aligned FASTA + `hmmbuild --informat afa` path.
- The generated HMM files were byte-identical.
- Verified `KOfamDownload.build_HMM_from_seqs()` produces a valid `HMMER3/` model.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89f6b109f7df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.