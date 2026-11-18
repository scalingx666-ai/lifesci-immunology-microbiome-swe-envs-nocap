# Issue

**Title:** Bump numpy from 1.16.4 to 1.17.0

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.16.4 to 1.17.0.
<details>
<summary>Release notes</summary>

*Sourced from [numpy's releases](https://github.com/numpy/numpy/releases).*

> ## v1.17.0
> NumPy 1.17.0 Release Notes
> ==========================
> 
> This NumPy release contains a number of new features that should substantially
> improve its performance and usefulness, see Highlights below for a summary. The
> Python versions supported are 3.5-3.7, note that Python 2.7 has been dropped.
> Python 3.8b2 should work with the released source packages, but there are no
> future guarantees.
> 
> Downstream developers should use Cython >= 0.29.11 for Python 3.8 support and
> OpenBLAS >= 3.7 (not currently out) to avoid problems on the Skylake
> architecture. The NumPy wheels on PyPI are built from the OpenBLAS development
> branch in order to avoid those problems.
> 
> 
> Highlights
> ==========
> 
> * A new extensible `random` module along with four selectable `random number
>   generators <random.BitGenerators>` and improved seeding designed for use in parallel
>   processes has been added. The currently available bit generators are `MT19937
>   <random.mt19937.MT19937>`, `PCG64 <random.pcg64.PCG64>`, `Philox
>   <random.philox.Philox>`, and `SFC64 <random.sfc64.SFC64>`. See below under
>   New Features.
> 
> * NumPy's `FFT <fft>` implementation was changed from fftpack to pocketfft,
>   resulting in faster, more accurate transforms and better handling of datasets
>   of prime length. See below under Improvements.
> 
> * New radix sort and timsort sorting methods. It is currently not possible to
>   choose which will be used. They are hardwired to the datatype and used
>   when either ``stable`` or ``mergesort`` is passed as the method. See below
>   under Improvements.
> 
> * Overriding numpy functions is now possible by default,
>   see ``__array_function__`` below.
> 
> 
> New functions
> =============
> 
> * `numpy.errstate` is now also a function decorator
> 
> 
> Deprecations
> ============
> 
> `numpy.polynomial` functions warn when passed ``float`` in place of ``int``
> ---------------------------------------------------------------------------
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  REL: NumPy 1.17.0 release.
-  Merge pull request  from charris/prepare-1.17.0-release
-  MAINT: Update mailmap and changelog for 1.17.0
-  Merge pull request  from charris/backport-14124
-  Merge pull request  from charris/backport-14091
-  Merge pull request  from charris/backport-14085
-  Merge pull request  from charris/backport-14048-14122
-  MAINT: Use equality instead of identity check with literal
-  MAINT: Remove unused import.
-  Addressed PR feedback
- Additional commits viewable in [compare view](https://github.com/numpy/numpy/compare/v1.16.4...v1.17.0)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.16.4&new-version=1.17.0)](https://dependabot.com/compatibility-score.html?dependency-name=numpy&package-manager=pip&previous-version=1.16.4&new-version=1.17.0)

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
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it). To ignore the version in this PR you can just close it
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a2e6d681238`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.