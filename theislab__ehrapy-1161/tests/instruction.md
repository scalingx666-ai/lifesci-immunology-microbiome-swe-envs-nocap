# Issue

**Title:** Add ep.tl.comorbidity_index for the Charlson and Elixhauser indices

## Description

`ep.tl.comorbidity_index` scores every patient with the Charlson or Elixhauser comorbidity index from ICD-9-CM and ICD-10 variables, and from SNOMED variables through the ICD codes mapped to them by `ed.annotate_codes` (theislab/ehrdata#317), using the Quan et al. 2005 coding algorithms with the Charlson, Quan 2011 or van Walraven weights. It stores the score and one column per comorbidity in `obs`, with the hierarchy rules applied so the score is their weighted sum, and warns about variables without any ICD code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `269c6bb07f8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.