# Issue

**Title:** build(deps-dev): bump sympy from 1.13.3 to 1.14.0

## Description

Bumps [sympy](https://github.com/sympy/sympy) from 1.13.3 to 1.14.0.
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>16fa855</code></a> Merge pull request <a href="">#28004</a> from oscarbenjamin/pr_bump_version_114</li>
<li><a href=""><code>597028e</code></a> release: bump version to 1.14.0 final</li>
<li><a href=""><code>db82759</code></a> Merge pull request <a href="">#27996</a> from oscarbenjamin/pr_27994_114_backport</li>
<li><a href=""><code>9861163</code></a> release: bump version to 1.14.0rc2</li>
<li><a href=""><code>d114acf</code></a> Revert passing init_printing settings to the pretty printer</li>
<li><a href=""><code>7f50681</code></a> Merge pull request <a href="">#27970</a> from oscarbenjamin/pr_benchmarks_114</li>
<li><a href=""><code>1721b69</code></a> maint(ci): fix paths in action</li>
<li><a href=""><code>fa12f64</code></a> maint(ci): fix benchmarks on 1.14 branch</li>
<li><a href=""><code>2b73e0c</code></a> Merge pull request <a href="">#27960</a> from oscarbenjamin/pr_pin_mpmath</li>
<li><a href=""><code>a66be8c</code></a> maint(ci): use Python 3.12 for flint==0.6.0</li>
<li>Additional commits viewable in <a href="https://github.com/sympy/sympy/compare/sympy-1.13.3...sympy-1.14.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=sympy&package-manager=pip&previous-version=1.13.3&new-version=1.14.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Summary by Sourcery

Build:
- Update sympy version in poetry.lock from 1.13.3 to 1.14.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfba07928069`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.