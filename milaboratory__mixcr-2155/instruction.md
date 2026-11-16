# Issue

**Title:** Regression tests changes in the develop

## Description

Automated changes generated after CI workflow run.

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=71910963"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

The snapshot updates appear safe to merge.

<h3>Summary</h3>

This PR updates four generated ONT analyze-preset snapshots to reflect the preset behavior merged immediately before it.
- **VDJRegion:** The V(D)J gene feature; it replaces `null` as both the subcloning and contig-assembly region in each snapshot.
- **OnlyUnambiguouslyCovering:** A contig post-filtering type; it replaces `NoFiltering` and is configured to check `VDJRegion`.
- **ONT presets:** The two generic presets receive the update directly; the two deprecated RNA-seq preset snapshots reflect inherited settings.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `564f2cbeaca7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.