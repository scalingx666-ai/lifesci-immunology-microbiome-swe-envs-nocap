# Issue

**Title:** Bump scipy from 1.2.1 to 1.3.0

## Description

Bumps [scipy](https://github.com/scipy/scipy) from 1.2.1 to 1.3.0.
<details>
<summary>Release notes</summary>

*Sourced from [scipy's releases](https://github.com/scipy/scipy/releases).*

> SciPy 1.3.0 Release Notes
> ================
> 
> SciPy 1.3.0 is the culmination of 5 months of hard work. It contains
> many new features, numerous bug-fixes, improved test coverage and better
> documentation. There have been some API changes
> in this release, which are documented below. All users are encouraged to
> upgrade to this release, as there are a large number of bug-fixes and
> optimizations. Before upgrading, we recommend that users check that
> their own code does not use deprecated SciPy functionality (to do so,
> run your code with ``python -Wd`` and check for ``DeprecationWarning`` s).
> Our development attention will now shift to bug-fix releases on the
> 1.3.x branch, and on adding new features on the master branch.
> 
> This release requires Python 3.5+ and NumPy 1.13.3 or greater.
> 
> For running on PyPy, PyPy3 6.0+ and NumPy 1.15.0 are required.
> 
> Highlights of this release
> --------------------------
> 
> - Three new ``stats`` functions, a rewrite of ``pearsonr``, and an exact
>   computation of the Kolmogorov-Smirnov two-sample test
> - A new Cython API for bounded scalar-function root-finders in `scipy.optimize`
> - Substantial ``CSR`` and ``CSC`` sparse matrix indexing performance
>   improvements
> - Added support for interpolation of rotations with continuous angular
>   rate and acceleration in ``RotationSpline``
> 
> 
> New features
> ============
> 
> `scipy.interpolate` improvements
> --------------------------------
> 
> A new class ``CubicHermiteSpline`` is introduced. It is a piecewise-cubic 
> interpolator which matches observed values and first derivatives. Existing 
> cubic interpolators ``CubicSpline``, ``PchipInterpolator`` and 
> ``Akima1DInterpolator`` were made subclasses of ``CubicHermiteSpline``.
> 
> `scipy.io` improvements
> -----------------------
> 
> For the Attribute-Relation File Format (ARFF) `scipy.io.arff.loadarff` 
> now supports relational attributes.
> 
> `scipy.io.mmread` can now parse Matrix Market format files with empty lines.
> 
> `scipy.linalg` improvements
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  REL: SciPy 1.3.0 release commit
-  Merge pull request  from tylerjereddy/scipy-130-rel-prep
-  TST: fix test issue for stats.pearsonr
-  MAINT: backport / prep for 1.3.0
-  REL: 1.3.0rc2 release commit
-  Merge pull request  from tylerjereddy/backports-130rc2-may8
-  BUG: fix linprog revised simplex docstring problem failure ()
-  MAINT: update scipy-sphinx-theme
-  MAINT: SciPy 1.3.0 rc2 preparation
-  REL: set version to 1.3.0rc1
- Additional commits viewable in [compare view](https://github.com/scipy/scipy/compare/v1.2.1...v1.3.0)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=scipy&package-manager=pip&previous-version=1.2.1&new-version=1.3.0)](https://dependabot.com/compatibility-score.html?dependency-name=scipy&package-manager=pip&previous-version=1.2.1&new-version=1.3.0)

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
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it yourself)
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71941035e10e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.