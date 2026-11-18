# Issue

**Title:** Trim by lib

## Description

This PR changes the behaviour of the bam_trim process, to allow separate trimming parameters not only by UDG treatment but also by library strandedness. This can be important for creating broader stable profiles that deal with complex datasets in a more transparent way. 
Also corrected the stated default value for bam trimming in the parameter helptext. The helptext stated 1 bp would be trimmed on each end, but the actual default was 0.

Added Parameters:
`bamutils_clip_double_stranded_half_udg_left`
`bamutils_clip_double_stranded_half_udg_right`
`bamutils_clip_double_stranded_none_udg_left`
`bamutils_clip_double_stranded_none_udg_right`
`bamutils_clip_single_stranded_half_udg_left`
`bamutils_clip_single_stranded_half_udg_right`
`bamutils_clip_single_stranded_none_udg_left`
`bamutils_clip_single_stranded_none_udg_right`

Removed Parameters:
`bamutils_clip_half_udg_left`
`bamutils_clip_half_udg_right`
`bamutils_clip_none_udg_left`
`bamutils_clip_none_udg_right`

<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core lint .`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19b14e0150f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.