# Issue

**Title:** MRG: update to sourmash v4.9.2

## Description

This is a patchfix to v4.9.1 () to deal with a botched source code release. Below are the updates since v4.9.0.

Minor new features:

* add cANI to `sig overlap` (#3644)

Bug fixes:

* make `RevIndex.len()` and `RevIndex.signatures()` use picklist, if set (#3647)

Cleanup and documentation updates:

* add rocksdb HOWTO (#3648)

Developer updates:

* try fixing inline variables in rust `println!` (#3640)

Dependabot updates:

- Build(deps): Update cachetools requirement from <6,>=4 to >=4,<7 (#3660)
- [pre-commit.ci] pre-commit autoupdate (#3659)
- Build(deps): Bump criterion from 0.5.1 to 0.6.0 (#3655)
- [pre-commit.ci] pre-commit autoupdate (#3654)
- Build(deps): Bump tempfile from 3.19.1 to 3.20.0 (#3639)
- [pre-commit.ci] pre-commit autoupdate (#3638)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5d614e2985f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.