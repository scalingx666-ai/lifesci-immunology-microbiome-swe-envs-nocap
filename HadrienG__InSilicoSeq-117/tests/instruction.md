# Issue

**Title:** Bump numpy from 1.17.1 to 1.17.2

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.17.1 to 1.17.2.
<details>
<summary>Release notes</summary>

*Sourced from [numpy's releases](https://github.com/numpy/numpy/releases).*

> ## v1.17.2
> NumPy 1.17.2 Release Notes
> ==========================
> 
> This release contains fixes for bugs reported against NumPy 1.17.1 along with a
> some documentation improvements. The most important fix is for lexsort when the
> keys are of type (u)int8 or (u)int16. If you are currently using 1.17 you
> should upgrade.
> 
> The Python versions supported in this release are 3.5-3.7, Python 2.7 has been
> dropped.  Python 3.8b4 should work with the released source packages, but there
> are no future guarantees.
> 
> Downstream developers should use Cython >= 0.29.13 for Python 3.8 support and
> OpenBLAS >= 3.7 to avoid errors on the Skylake architecture. The NumPy wheels
> on PyPI are built from the OpenBLAS development branch in order to avoid those
> errors.
> 
> 
> Contributors
> ============
> 
> A total of 7 people contributed to this release.  People with a "+" by their
> names contributed a patch for the first time.
> 
> * CakeWithSteak +
> * Charles Harris
> * Dan Allan
> * Hameer Abbasi
> * Lars Grueter
> * Matti Picus
> * Sebastian Berg
> 
> 
> Pull requests merged
> ====================
> 
> A total of 8 pull requests were merged for this release.
> 
> * : BUG: Fix aradixsort indirect indexing.
> * : DOC: Fix a minor typo in dispatch documentation.
> * : BUG: test, fix regression in converting to ctypes
> * : BUG: Do not show Override module in private error classes.
> * : BUG: Fixed maximum relative error reporting in assert_allclose.
> * : BUG: Fix uint-overflow if padding with linear_ramp and negative...
> * : BUG: Update 1.17.x with 1.18.0-dev pocketfft.py.
> * : REL: Prepare for NumPy 1.17.2 release.
> 
> Checksums
> =========
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  REL: NumPy 1.17.2 release.
-  Merge pull request  from charris/prepare-1.17.2-release
-  REL: Prepare for NumPy 1.17.2 release.
-  Merge pull request  from charris/backport-14279
-  MAINT: Update 1.17.x with 1.18.0-dev pocketfft.py.
-  Merge pull request  from charris/backport-14209
-  Merge pull request  from charris/backport-14429
-  Merge pull request  from charris/backport-13802
-  BUG: Fixed maximum relative error reporting in assert_allclose ([gh-13802](https://github-redirect.dependabot.com/numpy/numpy/issues/13802))
-  BUG: Replace _linear_ramp with linspace
- Additional commits viewable in [compare view](https://github.com/numpy/numpy/compare/v1.17.1...v1.17.2)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.17.1&new-version=1.17.2)](https://dependabot.com/compatibility-score.html?dependency-name=numpy&package-manager=pip&previous-version=1.17.1&new-version=1.17.2)

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
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Pull request limits (per update run and/or open at any time)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

Finally, you can contact us by mentioning @dependabot.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `276f7d2b181b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.