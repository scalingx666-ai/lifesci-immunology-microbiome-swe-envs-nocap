# Issue

**Title:** build(deps): bump pandas from 2.2.2 to 2.2.3

## Description

Bumps [pandas](https://github.com/pandas-dev/pandas) from 2.2.2 to 2.2.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pandas-dev/pandas/releases">pandas's releases</a>.</em></p>
<blockquote>
<h2>Pandas 2.2.3</h2>
<p>We are pleased to announce the release of pandas 2.2.3.
This release includes some new features, bug fixes, and performance improvements. We recommend that all users upgrade to this version.</p>
<p>See the <a href="https://pandas.pydata.org/pandas-docs/version/2.2.3/whatsnew/v2.2.3.html">full whatsnew</a> for a list of all the changes.
Pandas 2.2.3 supports Python 3.9 and higher.</p>
<p>The release will be available on the defaults and conda-forge channels:</p>
<pre><code>conda install pandas
</code></pre>
<p>Or via PyPI:</p>
<pre><code>python3 -m pip install --upgrade pandas
</code></pre>
<p>Please report any issues with the release on the <a href="https://github.com/pandas-dev/pandas/issues">pandas issue tracker</a>.</p>
<p>Thanks to all the contributors who made this release possible.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0691c5c</code></a> RLS: 2.2.3</li>
<li><a href=""><code>658dfdd</code></a> relax cython bound</li>
<li><a href=""><code>6891e90</code></a> Backport PR <a href="">#59847</a>: BLD: Build wheels for Python 3.13 on aarch64 as well</li>
<li><a href=""><code>f108468</code></a> RLS: 2.2.3</li>
<li><a href=""><code>6958738</code></a> Backport PR <a href="">#59840</a>: BLD: Final release prep for 2.2.3 (<a href="">#59842</a>)</li>
<li><a href=""><code>0bd98fe</code></a> Backport PR <a href="">#59136</a> on branch 2.2.x (Upload 3.13 &amp; free-threaded nightly wheel...</li>
<li><a href=""><code>8d67e77</code></a> Backport PR <a href="">#59836</a> on branch 2.2.x (BLD: Fix bad Cython annotation) (<a href="">#59837</a>)</li>
<li><a href=""><code>f7b6378</code></a> Assorted backports for 2.2.x (<a href="">#59785</a>)</li>
<li><a href=""><code>2127b42</code></a> Backport <a href="">#59144</a> on 2.2.x / 2.3.x (remove ops div class to solve <a href="">#2137</a>) (<a href="">#59535</a>)</li>
<li><a href=""><code>4a20adb</code></a> Backport PR <a href="">#59813</a> on branch 2.2.x (CI: Debug failing ARM builds) (<a href="">#59828</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pandas-dev/pandas/compare/v2.2.2...v2.2.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pandas&package-manager=pip&previous-version=2.2.2&new-version=2.2.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72423ff9ed26`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.