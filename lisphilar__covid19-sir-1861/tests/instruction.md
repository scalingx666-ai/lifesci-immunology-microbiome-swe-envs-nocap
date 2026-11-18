# Issue

**Title:** build(deps-dev): bump pytest-cov from 6.2.1 to 6.3.0

## Description

Bumps [pytest-cov](https://github.com/pytest-dev/pytest-cov) from 6.2.1 to 6.3.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest-cov/blob/master/CHANGELOG.rst">pytest-cov's changelog</a>.</em></p>
<blockquote>
<h2>6.3.0 (2025-09-06)</h2>
<ul>
<li>Added support for markdown reports.
Contributed by Marcos Boger in <code> &lt;</code>_
and <code> &lt;</code>_.</li>
<li>Fixed some formatting issues in docs.
Anonymous contribution in <code> &lt;</code>_.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a69d1ab</code></a> Bump version: 6.2.1 → 6.3.0</li>
<li><a href=""><code>475bf32</code></a> Update changelog.</li>
<li><a href=""><code>3834009</code></a> Add GitHub Actions example and fix example to not break with default markdown...</li>
<li><a href=""><code>0824728</code></a> Small phrasing adustments in Markdown docs</li>
<li><a href=""><code>474c1f4</code></a> Move markdown dest files check to StoreReport for earlier error and parser.er...</li>
<li><a href=""><code>7b21833</code></a> Default markdown-append to coverage.md and raise warning if both markdown opt...</li>
<li><a href=""><code>3a15312</code></a> Fix usage of Path.open() to write/append to files</li>
<li><a href=""><code>4b79449</code></a> Change output file cov-append.md in md-append example</li>
<li><a href=""><code>40e9e8e</code></a> Add docs and update AUTHORS.rst</li>
<li><a href=""><code>f5ca33a</code></a> Add tests for markdown and markdown-append</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest-cov/compare/v6.2.1...v6.3.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest-cov&package-manager=pip&previous-version=6.2.1&new-version=6.3.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd2d387fd160`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.