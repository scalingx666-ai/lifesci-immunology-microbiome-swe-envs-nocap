# Issue

**Title:** Assemble contigs by VDJRegion in ONT presets

## Description

generic-ont and generic-ont-with-umi -> Assembling contigs by VDJRegion

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=71635012"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 4/5</h2>

<!-- greptile-risk -->

The PR should not merge until the ONT preset flags and the preset consistency test agree.

<h2><a href="https://app.greptile.com/ide/claude-code?prompt=%23%23%23%20Issue%201%0Asrc%2Fmain%2Fresources%2Fpresets%2Fprotocols%2Fnanopore.yaml%3A14-15%0ABoth%20%60generic-ont%60%20and%20%60generic-ont-with-umi%60%20now%20select%20%60VDJRegion%60%20for%20contig%20assembly%2C%20but%20neither%20declares%20an%20%60assembleContigsBy%60%20flag.%20The%20preset%20consistency%20test%20requires%20that%20flag%20when%20a%20preset%20selects%20a%20contig-assembly%20feature%2C%20and%20these%20presets%20no%20longer%20qualify%20for%20its%20max-length%20exception.%20As%20a%20result%2C%20the%20test%20fails.%20Add%20the%20matching%20flag%2C%20or%20update%20the%20test%20if%20fixed-feature%20presets%20are%20meant%20to%20be%20exempt.%0A%0A---%0A%0AFor%20each%20issue%20above%2C%20determine%20whether%20it%20is%20valid%20and%20should%20be%20fixed.%20If%20so%2C%20fix%20it%20directly.&repo=milaboratory%2Fmixcr&pr=2154&platform=github"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInClaudeDark.svg?v=7"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInClaude.svg?v=7"><img alt="Fix All in Claude Code" src="https://greptile-static-assets.s3.amazonaws.com/badges/FixAllInClaude.svg?v=7" align="right"></picture></a>Findings</h2>

1. <img alt="P1" src="https://greptile-static-assets.s3.amazonaws.com/badges/p1.svg?v=9" align="top">&nbsp;**Missing contig assembly flag** <a href="">▶</a>

<details><summary>Fix with agent prompt</summary>

`````markdown
### Issue 1
src/main/resources/presets/protocols/nanopore.yaml:14-15
Both `generic-ont` and `generic-ont-with-umi` now select `VDJRegion` for contig assembly, but neither declares an `assembleContigsBy` flag. The preset consistency test requires that flag when a preset selects a contig-assembly feature, and these presets no longer qualify for its max-length exception. As a result, the test fails. Add the matching flag, or update the test if fixed-feature presets are meant to be exempt.

---

For each issue above, determine whether it is valid and should be fixed. If so, fix it directly.
`````

</details>

<h3>Summary</h3>

The PR changes `generic-ont` and `generic-ont-with-umi` from maximum-length contig assembly to assembly by `VDJRegion`, and documents that change.
- **Important touched terms:** `VDJRegion` is the selected gene feature defining the contig-assembly region; it becomes the feature for both presets. `SetContigAssemblingFeatures` is the preset mixin that selects assembly features; it replaces `AssembleContigsWithMaxLength`, the previous mixin requesting the longest possible contig. `generic-ont` and `generic-ont-with-umi` are the affected Oxford Nanopore presets, the latter including a UMI-processing step.

<!-- greptile_confidence_score:4 -->

<sub>Reviews (1) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7ca25f03092`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.