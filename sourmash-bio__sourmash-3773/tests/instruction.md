# Issue

**Title:** MRG: 4.9.4 release branch

## Description

Major new features:

* start writing v4->v5 migration docs (#3721)
* adjust warnings around tax abund and provide v5 upgrades to `tax metagenome`  (#3711)

Minor new features:

* try setting up --v4 and --v5 behavior differences for `sig check` (#3072)
* update `sig manifest` default rebuilding behavior for v5. (#3074)
* handle (ignore) empty taxids for `bioboxes` format (#3748)
* improve summary_csv for lingroups (#3758)

Cleanup and documentation updates:

* use auto-generated database list (#3754)

Developer updates:

* CI: fix dependabot config syntax, and clippy beta lints (#3762)
* CI: update to cibuildwheel 3.1.1 (#3738)
* ci: group dependabot updates by language (#3749)
* Remove docutils dep (#3769)
* bump version to 4.9.4-dev (#3715)
* disable WebAssembly builds, for now (#3724)

Dependabot updates:

* Build(ci): Bump actions/download-artifact from 4 to 5 (#3766)
* Build(deps): Bump DeterminateSystems/nix-installer-action from 17 to 18 (#3727)
* Build(deps): Bump DeterminateSystems/nix-installer-action from 18 to 19 (#3746)
* Build(deps): Bump criterion from 0.6.0 to 0.7.0 (#3741)
* Build(deps): Bump md5 from 0.7.0 to 0.8.0 (#3719)
* Build(deps): Bump memmap2 from 0.9.5 to 0.9.7 (#3732)
* Build(deps): Bump prefix-dev/setup-pixi from 0.8.10 to 0.8.11 (#3733)
* Build(deps): Bump prefix-dev/setup-pixi from 0.8.11 to 0.8.14 (#3747)
* Build(deps): Bump rand from 0.9.1 to 0.9.2 (#3743)
* Build(deps): Bump serde_json from 1.0.140 to 1.0.141 (#3742)
* [pre-commit.ci] pre-commit autoupdate (#3718)
* [pre-commit.ci] pre-commit autoupdate (#3725)
* [pre-commit.ci] pre-commit autoupdate (#3731)
* [pre-commit.ci] pre-commit autoupdate (#3737)
* [pre-commit.ci] pre-commit autoupdate (#3740)
* [pre-commit.ci] pre-commit autoupdate (#3756)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b34ce07709c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.