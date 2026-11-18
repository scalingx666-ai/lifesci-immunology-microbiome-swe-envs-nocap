# Issue

**Title:** Bump scipy from 1.1.0 to 1.2.1

## Description

Bumps [scipy](https://github.com/scipy/scipy) from 1.1.0 to 1.2.1.
<details>
<summary>Release notes</summary>

*Sourced from [scipy's releases](https://github.com/scipy/scipy/releases).*

> SciPy 1.2.1 Release Notes
> ==========================
> 
> SciPy `1.2.1` is a bug-fix release with no new features compared to `1.2.0`.
> Most importantly, it solves the issue that `1.2.0` cannot be installed
> from source on Python `2.7` because of non-ASCII character issues.
> 
> It is also notable that SciPy `1.2.1` wheels were built with OpenBLAS
> `0.3.5.dev`, which may alleviate some linear algebra issues observed
> in SciPy `1.2.0`.
> 
> Authors
> =======
> 
> * Eric Larson
> * Mark Mikofski
> * Evgeni Burovski
> * Ralf Gommers
> * Eric Moore
> * Tyler Reddy
>
> SciPy 1.2.0 Release Notes
> ==========================
> 
> SciPy 1.2.0 is the culmination of 6 months of hard work. It contains
> many new features, numerous bug-fixes, improved test coverage and better
> documentation. There have been a number of deprecations and API changes
> in this release, which are documented below. All users are encouraged to
> upgrade to this release, as there are a large number of bug-fixes and
> optimizations. Before upgrading, we recommend that users check that
> their own code does not use deprecated SciPy functionality (to do so,
> run your code with ``python -Wd`` and check for ``DeprecationWarning`` s).
> Our development attention will now shift to bug-fix releases on the
> 1.2.x branch, and on adding new features on the master branch.
> 
> This release requires Python 2.7 or 3.4+ and NumPy 1.8.2 or greater.
> 
> **Note**: This will be the last SciPy release to support Python 2.7.
>           Consequently, the 1.2.x series will be a long term support (LTS)
>           release; we will backport bug fixes until 1 Jan 2020.
> 
> For running on PyPy, PyPy3 6.0+ and NumPy 1.15.0 are required.
> 
> Highlights of this release
> ---------------------------
> 
> - 1-D root finding improvements with a new solver, ``toms748``, and a new
>   unified interface, ``root_scalar``
> - New ``dual_annealing`` optimization method that combines stochastic and
>   local deterministic searching
></tr></table> ... (truncated)
</details>
<details>
<summary>Commits</summary>

-  Merge pull request  from tylerjereddy/issue_9777
-  TST: xfail problematic test for 1.2.1 LTS
-  REL: 1.2.1 release commit
-  Merge pull request  from tylerjereddy/relnotes-121
-  TST: reduce max memory usage for sparse.linalg.lgmres test
-  DOC: update 1.2.1 release notes
-  Merge pull request  from tylerjereddy/backport-gh9739
-  BUG: qr_updates fails if u is exactly in span Q
-  Merge pull request  from tylerjereddy/backports_feb1_2019
-  TST: adjust to vmImage dispatch in Azure
- Additional commits viewable in [compare view](https://github.com/scipy/scipy/compare/v1.1.0...v1.2.1)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=scipy&package-manager=pip&previous-version=1.1.0&new-version=1.2.1)](https://dependabot.com/compatibility-score.html?dependency-name=scipy&package-manager=pip&previous-version=1.1.0&new-version=1.2.1)

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
- `@dependabot cancel merge` will cancel a previously requested merge
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `176162474a84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.