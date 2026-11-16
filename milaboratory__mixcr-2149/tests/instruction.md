# Issue

**Title:** Bump repseqio to 2.5.0-31-master (library v6.4)

## Description

Bumps repseqio to `2.5.0-31-master`, which makes RepSeq.IO library [v6.4](https://github.com/milaboratory/library/releases/tag/v6.4) the built-in default (milaboratory/repseqio#46).

- `build.gradle.kts`: `repseqioVersion` `2.5.0-14-master` → `2.5.0-31-master`
- `changelogs/v4.7.1.md`: new "Reference gene library changes" section
- `DefaultLibraryTest`: dog, pig, salmon and chicken resolve from the built-in library, with functional V and J (CDR3 anchors) for every chain

v6.4: new species dog, pig and Atlantic salmon (IGH, IGK, IGL, TRA/TRD, TRB, TRG), chicken IGL; corrected human IGH (`IGHV4-38-2` coordinates) and rabbit IGH, IGK, IGL. `repseqio.v6.3` stays available via `--library repseqio.v6.3`.

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=69821763"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-risk -->

The PR appears safe to merge; no actionable new issue or outstanding previous finding was established.

<h3>Summary</h3>

The PR updates RepSeq.IO so library v6.4 becomes the built-in default, documents the reference changes, and adds species-and-chain coverage tests.
- **RepSeq.IO library:** the dependency that supplies reference genes; its version changes to `2.5.0-31-master`.
- **Species and chains:** a taxon and its immunoglobulin or T-cell receptor loci; the new test checks dog, pig, salmon, and chicken against the updated default library.
- **Functional V/J genes and CDR3 anchors:** usable variable and joining genes with positions needed for CDR3 analysis; the test requires them for each listed chain.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (2) · Last reviewed commit: </sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71e1fb33667e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.