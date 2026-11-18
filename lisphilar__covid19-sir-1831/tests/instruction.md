# Issue

**Title:** build(deps-dev): bump setuptools from 78.1.0 to 78.1.1

## Description

Bumps [setuptools](https://github.com/pypa/setuptools) from 78.1.0 to 78.1.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pypa/setuptools/blob/main/NEWS.rst">setuptools's changelog</a>.</em></p>
<blockquote>
<h1>v78.1.1</h1>
<h2>Bugfixes</h2>
<ul>
<li>More fully sanitized the filename in PackageIndex._download. (<a href="">#4946</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8e4868a</code></a> Bump version: 78.1.0 → 78.1.1</li>
<li><a href=""><code>100e9a6</code></a> Merge pull request <a href="">#4951</a></li>
<li><a href=""><code>8faf1d7</code></a> Add news fragment.</li>
<li><a href=""><code>2ca4a9f</code></a> Rely on re.sub to perform the decision in one expression.</li>
<li><a href=""><code>e409e80</code></a> Extract _sanitize method for sanitizing the filename.</li>
<li><a href=""><code>250a6d1</code></a> Add a check to ensure the name resolves relative to the tmpdir.</li>
<li><a href=""><code>d8390fe</code></a> Extract _resolve_download_filename with test.</li>
<li><a href=""><code>4e1e893</code></a> Merge <a href="https://github.com/jaraco/skeleton">https://github.com/jaraco/skeleton</a></li>
<li><a href=""><code>3a3144f</code></a> Fix typo: <code>pyproject.license</code> -&gt; <code>project.license</code> (<a href="">#4931</a>)</li>
<li><a href=""><code>d751068</code></a> Fix typo: pyproject.license -&gt; project.license</li>
<li>Additional commits viewable in <a href="https://github.com/pypa/setuptools/compare/v78.1.0...v78.1.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=setuptools&package-manager=pip&previous-version=78.1.0&new-version=78.1.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lisphilar/covid19-sir/network/alerts).

</details>

## Summary by Sourcery

Bump development dependency setuptools from 78.1.0 to 78.1.1 in poetry.lock

Bug Fixes:
- Incorporate upstream fix to fully sanitize downloaded filenames in PackageIndex._download to prevent path traversal

Chores:
- Update setuptools version in development dependencies

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `590c36f1b139`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.