# Issue

**Title:** build(deps-dev): bump deptry from 0.23.1 to 0.24.0

## Description

Bumps [deptry](https://github.com/fpgmaas/deptry) from 0.23.1 to 0.24.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/releases">deptry's releases</a>.</em></p>
<blockquote>
<h2>0.24.0</h2>
<h2>What's Changed</h2>
<h3>Breaking changes</h3>
<h4>Python 3.9 support dropped</h4>
<p>Support for Python 3.9 has been dropped, as it has reached its end of life.</p>
<h4>PyPy 3.10 support dropped, 3.11 added</h4>
<p>Support for PyPy 3.10 has been dropped, since it is unsupported. We now only test against PyPy 3.11, and only publish wheels for this version.</p>
<h3>Features</h3>
<ul>
<li>Add GitHub Actions annotations reporter (<a href="">#1059</a>)</li>
<li>Add support for Python 3.14 (<a href="">#1224</a>)</li>
<li>Drop support for Python 3.9 (<a href="">#1328</a>)</li>
<li>Publish wheels for PyPy 3.11 and drop 3.10 (<a href="">#1227</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.23.1...0.24.0">https://github.com/fpgmaas/deptry/compare/0.23.1...0.24.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/blob/main/CHANGELOG.md">deptry's changelog</a>.</em></p>
<blockquote>
<h2>0.24.0 - 2025-11-09</h2>
<h3>Breaking changes</h3>
<h4>Python 3.9 support dropped</h4>
<p>Support for Python 3.9 has been dropped, as it has reached its end of life.</p>
<h4>PyPy 3.10 support dropped, 3.11 added</h4>
<p>Support for PyPy 3.10 has been dropped, since it is unsupported. We now only test against PyPy 3.11, and only publish wheels for this version.</p>
<h3>Features</h3>
<ul>
<li>Add GitHub Actions annotations reporter (<a href="">#1059</a>)</li>
<li>Add support for Python 3.14 (<a href="">#1224</a>)</li>
<li>Drop support for Python 3.9 (<a href="">#1328</a>)</li>
<li>Publish wheels for PyPy 3.11 and drop 3.10 (<a href="">#1227</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.23.1...0.24.0">https://github.com/fpgmaas/deptry/compare/0.23.1...0.24.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4cc2d65</code></a> docs(changelog): add 0.24.0 release notes (<a href="">#1330</a>)</li>
<li><a href=""><code>8757b31</code></a> chore: sync all dependency groups by default and run mypy locally (<a href="">#1337</a>)</li>
<li><a href=""><code>5ebc5c0</code></a> feat: add github annotations reporter (<a href="">#1059</a>)</li>
<li><a href=""><code>aa59b6f</code></a> fix(deps): update ruff rust to v0.14.4 (patch) (<a href="">#1335</a>)</li>
<li><a href=""><code>87a6b87</code></a> chore(deps): lock file maintenance (<a href="">#1336</a>)</li>
<li><a href=""><code>6b938ae</code></a> chore(deps): update uv-version to v0.9.8 (<a href="">#1334</a>)</li>
<li><a href=""><code>92c35ba</code></a> chore(deps): update pre-commit hook woodruffw/zizmor-pre-commit to v1.16.3 (#...</li>
<li><a href=""><code>a8be290</code></a> chore(deps): update pre-commit hook astral-sh/ruff-pre-commit to v0.14.4 (<a href="">#1332</a>)</li>
<li><a href=""><code>6abefd1</code></a> chore(deps): update dependency mkdocs-material to v9.6.23 (<a href="">#1331</a>)</li>
<li><a href=""><code>6b55686</code></a> test: update all test dependencies (<a href="">#1313</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/fpgmaas/deptry/compare/0.23.1...0.24.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=deptry&package-manager=pip&previous-version=0.23.1&new-version=0.24.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `534bcf526832`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.