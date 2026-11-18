# Issue

**Title:** Bump numpy from 1.17.0 to 1.17.1

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.17.0 to 1.17.1.
<details>
<summary>Release notes</summary>

*Sourced from [numpy's releases](https://github.com/numpy/numpy/releases).*

> ## v1.17.1
> NumPy 1.17.1 Release Notes
> ==========================
> 
> This release contains a number of fixes for bugs reported against NumPy 1.17.0
> along with a few documentation and build improvements.  The Python versions
> supported are 3.5-3.7, note that Python 2.7 has been dropped.  Python 3.8b3
> should work with the released source packages, but there are no future
> guarantees.
> 
> Downstream developers should use Cython >= 0.29.13 for Python 3.8 support and
> OpenBLAS >= 3.7 to avoid problems on the Skylake architecture. The NumPy wheels
> on PyPI are built from the OpenBLAS development branch in order to avoid those
> problems.
> 
> 
> Contributors
> ============
> 
> A total of 17 people contributed to this release.  People with a "+" by their
> names contributed a patch for the first time.
> 
> * Alexander Jung +
> * Allan Haldane
> * Charles Harris
> * Eric Wieser
> * Giuseppe Cuccu +
> * Hiroyuki V. Yamazaki
> * Jérémie du Boisberranger
> * Kmol Yuan +
> * Matti Picus
> * Max Bolingbroke +
> * Maxwell Aladago +
> * Oleksandr Pavlyk
> * Peter Andreas Entschev
> * Sergei Lebedev
> * Seth Troisi +
> * Vladimir Pershin +
> * Warren Weckesser
> 
> 
> Pull requests merged
> ====================
> 
> A total of 24 pull requests were merged for this release.
> 
> * : TST: Allow fuss in testing strided/non-strided exp/log loops
> * : BUG: avx2_scalef_ps must be static
> * : BUG: Remove stray print that causes a SystemError on python 3.7.
> * : BUG: Fix DeprecationWarning in python 3.8.
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  REL: NumPy 1.17.1 release.
-  Merge pull request  from charris/prepare-1.17.1-release
-  REL: Prepare for NumPy 1.17. release.
-  Merge pull request  from charris/backport-14310
-  MAINT: fix behavior of structured_to_unstructured on non-trivial dtypes
-  Merge pull request  from eric-wieser/fix-if-fields-1.17
-  Merge pull request  from charris/backport-14240
-  Merge remote-tracking branch 'upstream/maintenance/1.17.x' into fix-if-fields
-  BUG: don't fail when lexsorting some empty arrays ()
-  Merge pull request  from charris/backport-14241
- Additional commits viewable in [compare view](https://github.com/numpy/numpy/compare/v1.17.0...v1.17.1)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.17.0&new-version=1.17.1)](https://dependabot.com/compatibility-score.html?dependency-name=numpy&package-manager=pip&previous-version=1.17.0&new-version=1.17.1)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f89bab1f2156`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.