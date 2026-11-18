# Issue

**Title:** Bump ehrdata to 5477294 and the tutorials to the subgroups tutorial

## Description

Moves ehrdata to main with rebin, from_events, read_meds/write_meds, read_fhir and annotate_codes/aggregate_codes (theislab/ehrdata#313-#317) and the analysis-ready PhysioNet loaders (theislab/ehrdata#318), and the tutorials to the cohort tutorial adapted to them (theislab/ehrapy-tutorials#79) and the new subgroups tutorial (theislab/ehrapy-tutorials#78), which replaces mimic_2_introduction in the gallery, notebook CI and via a redirect.
The notebook CI thereby runs every tutorial against the new PhysioNet contents, where `Gender` and `ICUType` are labelled categoricals and `-1` placeholders are missing values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0655a5b94b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.