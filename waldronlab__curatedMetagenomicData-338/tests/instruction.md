# Issue

**Title:** ci: replace rworkflows with the Bioconductor reusable workflow

## Description

## Summary

`rworkflows` has been failing on `devel` since at least 2026-07-30 — all three OS jobs — so the check has given no usable signal for months. This swaps it for [`bioconductor/workflows`](https://github.com/Bioconductor/workflows), which runs the official Bioconductor `R CMD check` and `BiocCheck` inside the `bioconductor_docker` container.

The whole workflow is now 22 lines calling a reusable one, replacing 57 lines of matrix config.

## What changes

- Drops the third-party `neurogenomics/rworkflows@master` dependency, and with it `permissions: write-all`. Permissions are now the three the reusable workflow actually needs (`contents: read`, `pages: write`, `id-token: write` — declaring any permissions zeroes the rest, which is why `contents: read` is listed explicitly).
- `error_on: 'warning'`, matching the Bioconductor default. **This will likely be red at first**, and that's deliberate — it reflects the package's real state rather than a threshold chosen to produce green.
- `enable_pkgdown: true`, plus `workflow_dispatch`. The reusable workflow builds and deploys pkgdown on `RELEASE_*` branches only, which is the right source for a public docs site. It won't fire on `devel`; dispatching on a release branch rebuilds the site on demand. Note this workflow file has to exist on a release branch before it can be dispatched there.
- Codecov stays wired up — `CODECOV_TOKEN` is already a repo secret, and the reusable workflow skips coverage when it's absent or on a release branch.

## Deliberate regression

macOS and Windows coverage is dropped: `bioccheck.yml` is Linux-only. The Bioconductor build system already checks those platforms for released packages, and [`r-universe-org/workflows`](https://github.com/r-universe-org/workflows) with `organization: bioconductor` is the documented route if we want them back locally. Recording it here so it's a decision rather than an accident.

## Note

`bioconductor/workflows` is pre-release — the README says a stable `v1` tag is coming and some things may not work yet. This pins `@main`, per the upstream template, so we track fixes and can file issues upstream. Worth pinning to a tag once `v1` lands.

.

## Test plan

- [ ] The `Bioconductor CI` workflow triggers on this PR and runs to completion
- [ ] Review the `R CMD check` / `BiocCheck` output — expect real findings, since rworkflows has been red for months
- [ ] Confirm Codecov upload succeeds

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `116ac707bf8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.