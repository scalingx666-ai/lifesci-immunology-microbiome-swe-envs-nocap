# Issue

**Title:** Retain read group info

## Description

#808 

Changes: 
- When mapping, assign the `SM` field of read groups to the sample name instead of the library Id. 
- Deactivate replacement of read headers upon library merging.
- Flexible filtering for map and base quality when genotyping with pileupcaller.

This combination (in my small testing case) skips all the fiddling with read groups manually, retains all read group information and still produces a single genotyped individual per BAM within gatk UG.

Still testing a couple of things, but this should retain all the library/sequencing information within the final bams produced. 
 
Added Parameters:
- `pileupcaller_min_map_quality`. Default is 30. Changes the minimum mapping quality used in mpileup creation for pileupcaller. Affects samtools mpileup `-q` parameter.
- `pileupcaller_min_base_quality`. Default is 30. Changes the minimum base quality used in mpileup creation for pileupcaller. Affects samtools mpileup `-Q` parameter.

<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] Make sure your code lints (`nf-core lint .`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2e22568613a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.