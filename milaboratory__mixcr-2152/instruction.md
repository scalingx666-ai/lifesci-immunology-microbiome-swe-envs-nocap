# Issue

**Title:** itests: update case008/case009 expectations for V maxHits 15

## Description

Every `develop` build since #2145 has failed `:test (int)` case008 and case009:

```
expected "241364" got "241395" for cat case8.align.report.json | head -n 1 | jq -r .chainUsage.chains.TRA.total
```

#2145 raised the per-mate V `maxHits` to 15 in the `generic-amplicon` align preset, which changes the counts. This PR updates the expectations to the values the current build produces, measured with the `develop` build artifact (`21bd40be`) on the CI test data:

| value | case008 | case009 |
|---|---|---|
| TRA total | 241364 → 241395 | 241364 → 241395 |
| readsInClones | 200784 → 200812 | 200784 → 200812 |
| clones | 25662 → 25664 | – |
| clonesWithAmbiguousLetters | 3547 → 3548 | 3547 → 3548 |
| finalCloneCount | 25662 → 25664 | 25662 → 25664 |

The values are identical with `--library repseqio.v6.4`, so they come from the preset change, not the library update (#2150). Both scripts pass locally with the new values.

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=71215898"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

The expectation updates appear safe to merge.

<h3>Summary</h3>

The PR updates case008 and case009 integration-test expectations after the `generic-amplicon` preset raised per-mate V `maxHits` to 15.
- **TRA total:** the reported count of TRA-chain alignments; both expected totals change from 241364 to 241395.
- **readsInClones:** reads assigned to clones; both expectations change from 200784 to 200812.
- **clones / finalCloneCount:** clone counts at assembly and after contig assembly; the affected expectations change from 25662 to 25664.
- **clonesWithAmbiguousLetters:** contig-assembly clones containing ambiguous letters; both expectations change from 3547 to 3548.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7691aafe90c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.