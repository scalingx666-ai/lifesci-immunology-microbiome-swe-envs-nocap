# Issue

**Title:** MILAB-7239: rebuild software image on amazoncorretto:21-al2023

## Description

Part of MILAB-7239 (update custom images of block software after the eMudhra intermediate CA compromise, October 2026).

## Why

The old `amazoncorretto:21` image (Amazon Linux 2, Corretto 21.0.11) uses the JDK bundled `cacerts`. That trust store has the `AAA Certificate Services` root. The compromised eMudhra intermediates (EM DV/OV/EV TLS CA - G3B/G3C) have cross-certificates from this root. Thus, Java in the old image trusts certificates that these compromised CAs issue.

The current `amazoncorretto:21` image (Amazon Linux 2023, Corretto 21.0.12.1) uses the system trust store, which does not have this root. A test with `X509TrustManager.checkServerTrusted()` gave these results:

| Image | Chains through the AAA cross-certificate |
|---|---|
| `amazoncorretto:21.0.11` (AL2) | 3 of 3 trusted: vulnerable |
| `amazoncorretto:21` = `21-al2023` (AL2023, 2026-10-23) | 3 of 3 rejected |

## Change

- `FROM amazoncorretto:21` -> `FROM amazoncorretto:21-al2023`. Today both tags point to the same image. The explicit tag makes sure that future rebuilds keep the AL2023 system trust store.
- The merge triggers a new package build. CI pulls the fresh base image, and the image tag is content-addressed, so the package gets a new image.

## After merge

Update the blocks that use this software package to the new version.

<!-- greptile_comment -->

<!-- greptile_summary -->

<h2><a href="https://app.greptile.com/api/retrigger?id=86731524"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/RetriggerDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2"><img alt="Retrigger" src="https://greptile-static-assets.s3.amazonaws.com/badges/Retrigger.svg?v=2" align="right"></picture></a><a href="https://app.greptile.com/milaboratories/github/milaboratory/mixcr/-/pull/2167"><picture><source media="(prefers-color-scheme: dark)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptileDark.svg?v=2"><source media="(prefers-color-scheme: light)" srcset="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2"><img alt="View in Greptile" src="https://greptile-static-assets.s3.amazonaws.com/badges/ViewInGreptile.svg?v=2" align="right"></picture></a>Confidence Score: 5/5</h2>

<!-- greptile-impact-verdict --> The PR appears safe to merge; no actionable issues were found.

<h3>Summary</h3>

Changes `pl-pkg/Dockerfile` to use `amazoncorretto:21-al2023` instead of `amazoncorretto:21`.
- The Platforma Docker package now builds on Amazon Linux 2023 Corretto 21.

Important touched terms:
- **Base image** — the starting container image that supplies Java and the operating system. Its reference changes to `amazoncorretto:21-al2023`.
- No code types are changed.

<!-- greptile_confidence_score:5 -->

<sub>Reviews (1) · Last reviewed commit:  · [Reviewed by Greptile](https://www.greptile.com/?utm_source=greptile_review&utm_medium=github&utm_campaign=review_public&utm_content=milaboratory/mixcr)</sub>

<!-- /greptile_comment -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a839f44a313`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.