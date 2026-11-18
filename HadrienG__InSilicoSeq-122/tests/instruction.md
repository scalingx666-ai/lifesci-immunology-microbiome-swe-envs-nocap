# Issue

**Title:** Bump numpy from 1.17.2 to 1.17.3

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.17.2 to 1.17.3.
<details>
<summary>Release notes</summary>

*Sourced from [numpy's releases](https://github.com/numpy/numpy/releases).*

> ## v1.17.3
> NumPy 1.17.3 Release Notes
> ==========================
> 
> This release contains fixes for bugs reported against NumPy 1.17.2 along with a
> some documentation improvements. The Python versions supported in this release 
> are 3.5-3.8.
> 
> Downstream developers should use Cython >= 0.29.13 for Python 3.8 support and
> OpenBLAS >= 3.7 to avoid errors on the Skylake architecture.
> 
> 
> Highlights
> ==========
> 
> - Wheels for Python 3.8
> - Boolean ``matmul`` fixed to use booleans instead of integers.
> 
> 
> Compatibility notes
> ===================
> 
> - The seldom used ``PyArray_DescrCheck`` macro has been changed/fixed.
> 
> 
> Contributors
> ============
> 
> A total of 7 people contributed to this release.  People with a "+" by their
> names contributed a patch for the first time.
> 
> * Allan Haldane
> * Charles Harris
> * Kevin Sheppard
> * Matti Picus
> * Ralf Gommers
> * Sebastian Berg
> * Warren Weckesser
> 
> 
> Pull requests merged
> ====================
> 
> A total of 12 pull requests were merged for this release.
> 
> * : MAINT: clean up pocketfft modules inside numpy.fft namespace.
> * : BUG: random.hypergeometic assumes npy_long is npy_int64, hung...
> * : BUG: random: Revert [gh-14458](https://github-redirect.dependabot.com/numpy/numpy/issues/14458) and refix [gh-14557](https://github-redirect.dependabot.com/numpy/numpy/issues/14557).
> * : BUG: add a specialized loop for boolean matmul.
> * : MAINT: Update pytest version for Python 3.8
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  REL: NumPy 1.14.5 release.
-  Merge pull request  from charris/prepare-1.17.3-release
-  REL: Prepare for 1.17.3 release.
-  Merge pull request  from charris/backport-14605
-  BUG: properly define PyArray_DescrCheck
-  Merge pull request  from charris/backport-14531
-  BUG: random: Create a legacy implementation of random.binomial.
-  Merge pull request  from rgommers/bport-fftlicense
-  DOC: remove note about Pocketfft license file (non-existing here).
-  Merge pull request  from charris/backport-14498
- Additional commits viewable in [compare view](https://github.com/numpy/numpy/compare/v1.17.2...v1.17.3)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.17.2&new-version=1.17.3)](https://dependabot.com/compatibility-score.html?dependency-name=numpy&package-manager=pip&previous-version=1.17.2&new-version=1.17.3)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03e60a56f47a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.