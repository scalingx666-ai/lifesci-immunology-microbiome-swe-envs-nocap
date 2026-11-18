# Issue

**Title:** build(deps-dev): update deptry requirement from <0.25,>=0.12 to >=0.12,<0.26

## Description

Updates the requirements on [deptry](https://github.com/osprey-oss/deptry) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/osprey-oss/deptry/releases">deptry's releases</a>.</em></p>
<blockquote>
<h2>0.25.1</h2>
<h2>What's Changed</h2>
<p>Release <a href="https://github.com/osprey-oss/deptry/releases/tag/0.25.0">0.25.0</a> was yanked in PyPI because of a failure during the release. 0.25.1 is identical, but includes a fix in the release process.</p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/osprey-oss/deptry/compare/0.25.0...0.25.1">https://github.com/osprey-oss/deptry/compare/0.25.0...0.25.1</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/osprey-oss/deptry/blob/main/CHANGELOG.md">deptry's changelog</a>.</em></p>
<blockquote>
<h2>0.25.1 - 2025-03-18</h2>
<p>Release 0.25.0 was yanked in PyPI because of a failure during the release. 0.25.1 is identical, but includes a fix in the release process.</p>
<h2>0.25.0 - 2025-03-18</h2>
<h3>Repository moved to Osprey OSS</h3>
<p>deptry has moved from <a href="https://github.com/fpgmaas/deptry">fpgmaas/deptry</a> to <a href="https://github.com/osprey-oss/deptry">osprey-oss/deptry</a> under the new Osprey OSS organisation. This ensures the project is not tied to a single account and makes it easier to manage contributors and access as the project grows.</p>
<h3>Features</h3>
<ul>
<li>Support inline <code># deptry: ignore</code> comments to suppress violations (<a href="">#1473</a>)</li>
<li>Support non-dev dependency groups with <code>--non-dev-dependency-groups</code> (<a href="">#1440</a>)</li>
<li>Use <code>tomli</code> on Python &lt; 3.15 for TOML 1.1 support (<a href="">#1446</a>)</li>
<li>Add <code>--optional-dependencies-dev-groups</code> and deprecate <code>--pep621-dev-dependency-groups</code> (<a href="">#1391</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>Ensure that <code>--config</code> does not suppress output (<a href="">#1390</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.24.0...0.25.0">https://github.com/fpgmaas/deptry/compare/0.24.0...0.25.0</a></p>
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
<p><a href="https://github.com/osprey-oss/deptry/compare/0.23.1...0.24.0">https://github.com/osprey-oss/deptry/compare/0.23.1...0.24.0</a></p>
<h2>0.23.1 - 2025-07-30</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0c39226</code></a> Remove pinned maturin version for building windows wheels in release (<a href="">#1516</a>)</li>
<li><a href=""><code>501a929</code></a> chore(packaging): use PEP 639 license format (<a href="">#1514</a>)</li>
<li><a href=""><code>2d89cf4</code></a> Releasenotes for release 0.25.0 (<a href="">#1510</a>)</li>
<li><a href=""><code>ef64f93</code></a> Replace all references of fpgmaas/deptry with osprey-oss/deptry (<a href="">#1513</a>)</li>
<li><a href=""><code>fdec8c5</code></a> Add trusted publishing (<a href="">#1512</a>)</li>
<li><a href=""><code>2e27ae2</code></a> chore(deps): update uv-version to v0.10.10 (<a href="">#1503</a>)</li>
<li><a href=""><code>9d1f7d1</code></a> chore(deps): update pre-commit hook astral-sh/ruff-pre-commit to v0.15.6 (<a href="">#1502</a>)</li>
<li><a href=""><code>2a5a0a6</code></a> chore(deps): update dependency mkdocs-material to v9.7.5 (<a href="">#1501</a>)</li>
<li><a href=""><code>487f682</code></a> chore(deps): update dependency pnpm to v10.32.1 (<a href="">#1506</a>)</li>
<li><a href=""><code>608ba46</code></a> fix(deps): update ruff rust to v0.15.6 (<a href="">#1504</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/osprey-oss/deptry/compare/0.12.0...0.25.1">compare view</a></li>
</ul>
</details>
<br />

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ee7271d4681`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.