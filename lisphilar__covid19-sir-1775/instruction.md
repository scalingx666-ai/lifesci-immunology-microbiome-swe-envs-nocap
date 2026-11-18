# Issue

**Title:** build(deps-dev): bump deptry from 0.21.0 to 0.21.1

## Description

Bumps [deptry](https://github.com/fpgmaas/deptry) from 0.21.0 to 0.21.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/releases">deptry's releases</a>.</em></p>
<blockquote>
<h2>0.21.1</h2>
<h2>What's Changed</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Handle string requirements files for <code>setuptools</code> dynamic dependencies (<a href="">#945</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/fpgmaas/deptry/compare/0.21.0...0.21.1">https://github.com/fpgmaas/deptry/compare/0.21.0...0.21.1</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/blob/main/CHANGELOG.md">deptry's changelog</a>.</em></p>
<blockquote>
<h2>0.21.1 - 2024-11-15</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Handle string requirements files for <code>setuptools</code> dynamic
dependencies (<a href="">#945</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.21.0...0.21.1">https://github.com/fpgmaas/deptry/compare/0.21.0...0.21.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>54b54a0</code></a> docs(changelog): add 0.21.1 release notes (<a href="">#946</a>)</li>
<li><a href=""><code>2a9da88</code></a> fix(dependency_getter): handle strings for <code>setuptools</code> dynamic dependencies ...</li>
<li><a href=""><code>40765df</code></a> chore(deps): lock file maintenance (<a href="">#943</a>)</li>
<li><a href=""><code>c7b7a07</code></a> chore(deps): lock file maintenance (<a href="">#942</a>)</li>
<li><a href=""><code>b4f5bb4</code></a> fix(deps): update rust crate pyo3 to v0.22.6 (<a href="">#940</a>)</li>
<li><a href=""><code>78697aa</code></a> chore(deps): update uv-version to v0.5.1 (<a href="">#941</a>)</li>
<li><a href=""><code>af07798</code></a> chore(deps): update uv-version to v0.4.30 (<a href="">#939</a>)</li>
<li><a href=""><code>f200460</code></a> chore(deps): update pre-commit hook astral-sh/ruff-pre-commit to v0.7.3 (<a href="">#938</a>)</li>
<li><a href=""><code>a59e388</code></a> chore(deps): update dependency mkdocs-material to v9.5.44 (<a href="">#937</a>)</li>
<li>See full diff in <a href="https://github.com/fpgmaas/deptry/compare/0.21.0...0.21.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=deptry&package-manager=pip&previous-version=0.21.0&new-version=0.21.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump deptry from version 0.21.0 to 0.21.1 to include the latest bug fixes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `baae8a89b229`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.