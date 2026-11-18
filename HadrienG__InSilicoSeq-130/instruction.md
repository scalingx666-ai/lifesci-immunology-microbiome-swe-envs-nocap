# Issue

**Title:** Bump numpy from 1.17.3 to 1.17.4

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.17.3 to 1.17.4.
<details>
<summary>Release notes</summary>

*Sourced from [numpy's releases](https://github.com/numpy/numpy/releases).*

> ## v1.17.4
> NumPy 1.17.4 Release Notes
> ==========================
> 
> This release contains fixes for bugs reported against NumPy 1.17.3 along with
> some build improvements. The Python versions supported in this release
> are 3.5-3.8.
> 
> Downstream developers should use Cython >= 0.29.13 for Python 3.8 support and
> OpenBLAS >= 3.7 to avoid errors on the Skylake architecture.
> 
> 
> Highlights
> ==========
> 
> * Fixed `np.random.random_integers` biased generation of 8 and 16 bit integers.
> * Fixed `np.einsum` regression on Power9 and z/Linux.
> * Fixed histogram problem with signed integer arrays.
> 
> 
> Contributors
> ============
> 
> A total of 5 people contributed to this release.  People with a "+" by their
> names contributed a patch for the first time.
> 
> * Charles Harris
> * Chris Burr +
> * Matti Picus
> * Qiming Sun +
> * Warren Weckesser
> 
> 
> Pull requests merged
> ====================
> 
> A total of 8 pull requests were merged for this release.
> 
> * : BLD: declare support for python 3.8
> * : BUG: random: biased samples from integers() with 8 or 16 bit...
> * : BUG: Fix _ctypes class circular reference. ()
> * : BLD: add 'apt update' to shippable
> * : BUG: Fix `np.einsum` errors on Power9 Linux and z/Linux
> * : BUG: lib: Fix histogram problem with signed integer arrays.
> * : BLD: Prevent -flto from optimising long double representation...
> * : MAINT: move buffer.h -> npy_buffer.h to avoid conflicts
> 
> 
> Checksums
> =========
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  REL: NumPy 1.17.4 release.
-  Merge pull request  from charris/prepare-1.17.4-release
-  REL: Prepare for 1.17.4 release.
-  Merge pull request  from charris/backport-14830
-  MAINT: move buffer.h -> npy_buffer.h to avoid conflicts
-  Merge pull request  from charris/backport-14827
-  Merge pull request  from charris/backport-14381
-  BLD: Review feedback for clang -flto fix
-  BLD: Prevent -flto from optimising long double representation check away
-  BUG: lib: Fix histogram problem with signed integer arrays.
- Additional commits viewable in [compare view](https://github.com/numpy/numpy/compare/v1.17.3...v1.17.4)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.17.3&new-version=1.17.4)](https://dependabot.com/compatibility-score.html?dependency-name=numpy&package-manager=pip&previous-version=1.17.3&new-version=1.17.4)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Pull request limits (per update run and/or open at any time)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `681ee9625efa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.