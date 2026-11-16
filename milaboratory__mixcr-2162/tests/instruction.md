# Issue

**Title:** Make available the miltenyi-human-rna-bcr-profiling preset

## Description

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=75403619"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

The PR appears safe to merge; no actionable issues were found.

What we checked:
- Missing settings for a stage: The parent supplies settings for all four selected stages. The child overrides alignment and UMI refinement while retaining assembly and export settings.

<h3>Summary</h3>

Enables `miltenyi-human-rna-bcr-profiling` by uncommenting its existing definition. Users can select the Miltenyi Human BCR RNA Profiling Kit preset for alignment, UMI refinement, clone assembly, and export.

Important touched types:
- `SetSpecies` sets the sample species. The enabled preset selects human (`hsa`).
- `MaterialTypeRNA` selects RNA-specific settings. It now applies to this preset.
- `SetTagPattern` defines how reads contain tags and sequences. The enabled pattern extracts a 14-base `UMI` and the `R1` and `R2` sequences.
- `SetClonotypeAssemblingFeatures` selects the sequence span used to assemble clones. The preset enables `{CDR1Begin:FR4End}`.
- `SetSplitClonesBy` keeps clones separate by the selected gene type. The preset enables splitting by `C`.
- `AddExportClonesField` adds a field to clone exports. The preset enables `-isotype` with `auto`.

No actionable issues were found. Checks were based on source review; no tests were run.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04ab37f8b24f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.