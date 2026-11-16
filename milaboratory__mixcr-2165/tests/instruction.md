# Issue

**Title:** MILAB-6874: estimatedInitialClones in the align report

## Description

## What

Companion to milaboratory/mixcr-algo#155 (merged, `4.7.0-81-develop`). `mixcr align` now writes `estimatedInitialClones` to its report: a HyperLogLog estimate of `assemble`'s `initialClonesCreated`, for sizing assemble's memory before it runs. The field is null when the bundle has no assemble step.

`CommandAlign` passes the bundle's `cloneAssemblerParameters` to `AlignerReportBuilder.setClonotypeEstimationParameters`; mixins are already applied, so `--assemble-clonotypes-by` and `--split-clones-by` are folded in.

## Verification

- `RunMiXCRTest.alignEstimatesAssembleInitialClones`: estimate within 2 of assemble's real count on `sample_IGH`. Passes.
- itest `case-align_initial_clones_estimate`: generic-amplicon on CD4M1, estimate within 5 % of `initialClonesCreated`. Locally 25469 vs 25647 (0.7 %).

## Regression

The report schema and the regression yamls gain the new field; CI's automated regression commit regenerates them.

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=84298565"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a><a href="https://app.greptile.com/milaboratories/github/milaboratory/mixcr/-/pull/2165"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptileDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2"><img alt="View in Greptile" src="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-impact-verdict --> The PR appears safe to merge; no actionable defects were established.

<h3>Summary</h3>

Adds `estimatedInitialClones` to alignment reports to help size memory before assembly.
- Align reports estimate the initial clone count assemble will create.

Important touched types:
- `CommandAlign`: Runs alignment. It now passes the bundle’s assembly settings to the report builder.
- `AlignerReportBuilder`: Collects alignment results for reports. It now receives settings through `setClonotypeEstimationParameters`.
- `RunMiXCR.AlignResult`: Holds alignment results and their report. The new Java test reads its estimate.
- `RunMiXCR.AssembleResult`: Holds assembly results and their report. The new test uses its actual initial clone count for comparison.

No actionable defects were established. Tests were not run during this review.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit:  · [Reviewed by Greptile](https://www.greptile.com/?utm_source=greptile_review&utm_medium=github&utm_campaign=review_public&utm_content=milaboratory/mixcr)</sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75569995d094`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.