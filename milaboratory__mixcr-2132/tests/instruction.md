# Issue

**Title:** MILAB-6872: unpin pl-pkg from package-builder 3.8.0

## Description

## Why

CI installs `pl-pkg` with `npm ci`, so `package-lock.json` decided the builder version: **3.8.0**, while the declared range `^3.8.0` has been resolving to 3.15.0 for anyone doing a fresh install. 3.8.0 predates every guard that makes a silent docker-push failure visible:

| Version | What it adds |
|---|---|
| 3.15.0 | `assertDockerPushIntent` — a CI run that builds images without pushing them is an error, instead of a green build whose published `.sw.json` descriptors point at images nobody can pull |
| 3.11.6 | publish *all* docker packages, not just buildable archive ones |
| 3.13.0 | stable image digests (provenance/SBOM off), so the already-pushed smart-skip actually matches |

Confirmed against the tarballs: 3.8.0 ships no `push-guard`; 3.15.0 wires it into `commands/build/all.js` and `commands/build/docker.js`.

Context: while investigating a MiXCR failure we went looking for an unpushed image. The image turned out to be present upstream — but nothing in this release path would have told us either way.

## What

`pl-pkg/package.json` → `^3.15.0`, lockfile refreshed. The lock shrinks a lot because 3.14.0 moved the CLI from oclif to commander, so that dependency tree is gone.

## Checked locally

`npm ci` installs clean on the new lock (229 packages) and `pl-pkg --help` still exposes the `build` / `prepublish` / `publish` surface this package's scripts use.

Pairs with milaboratory/github-ci#201, which gates publication on the images actually being in the registry for packages released through `java-gradle.yaml`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00eb424cfcc3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.