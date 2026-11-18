# Issue

**Title:** build(deps-dev): bump deptry from 0.21.2 to 0.22.0

## Description

Bumps [deptry](https://github.com/fpgmaas/deptry) from 0.21.2 to 0.22.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/releases">deptry's releases</a>.</em></p>
<blockquote>
<h2>0.22.0</h2>
<h2>What's Changed</h2>
<p>Poetry 2.0 introduced support for <a href="https://python-poetry.org/blog/announcing-poetry-2.0.0/">defining project metadata using PEP 621</a>. This is now supported by <em>deptry</em>. <a href="https://deptry.com/supported-dependency-managers/#poetry">Documentation</a> has been updated to detail <em>deptry</em>'s behavior.</p>
<h3>Features</h3>
<ul>
<li>Support PEP 621 in Poetry 2.0+ (<a href="">#1003</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/fpgmaas/deptry/compare/0.21.2...0.22.0">https://github.com/fpgmaas/deptry/compare/0.21.2...0.22.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/blob/main/CHANGELOG.md">deptry's changelog</a>.</em></p>
<blockquote>
<h2>0.22.0 - 2025-01-10</h2>
<p>Poetry 2.0 introduced support
for <a href="https://python-poetry.org/blog/announcing-poetry-2.0.0/">defining project metadata in PEP 621</a>. This is now
supported by <em>deptry</em>. <a href="https://deptry.com/supported-dependency-managers/#poetry">Documentation</a> has been updated to
detail <em>deptry</em>'s behavior.</p>
<h3>Features</h3>
<ul>
<li>Support PEP 621 in Poetry 2.0+ (<a href="">#1003</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.21.2...0.22.0">https://github.com/fpgmaas/deptry/compare/0.21.2...0.22.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>875d58e</code></a> docs(changelog): add 0.22.0 release notes (<a href="">#1011</a>)</li>
<li><a href=""><code>60c0658</code></a> feat(poetry): support PEP 621 in Poetry 2.0+ (<a href="">#1003</a>)</li>
<li><a href=""><code>26511d8</code></a> chore: bump rust to 1.84 (<a href="">#1010</a>)</li>
<li><a href=""><code>b9ace6d</code></a> chore(deps): update dependency poetry to v2 (<a href="">#1007</a>)</li>
<li><a href=""><code>3e0623d</code></a> test(functional): avoid installing tools in tests (<a href="">#1008</a>)</li>
<li><a href=""><code>1a00e27</code></a> perf(dependency_getter): search for uv before PDM (<a href="">#1004</a>)</li>
<li><a href=""><code>6e7646b</code></a> test(functional): pin versions of tools (<a href="">#1006</a>)</li>
<li><a href=""><code>29f1455</code></a> chore(deps): lock file maintenance (<a href="">#1001</a>)</li>
<li><a href=""><code>cf1942f</code></a> chore(deps): update pre-commit hook woodruffw/zizmor-pre-commit to v1 (<a href="">#1000</a>)</li>
<li><a href=""><code>4920429</code></a> chore(deps): update pre-commit hook astral-sh/ruff-pre-commit to v0.8.5 (<a href="">#998</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/fpgmaas/deptry/compare/0.21.2...0.22.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=deptry&package-manager=pip&previous-version=0.21.2&new-version=0.22.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump deptry from 0.21.2 to 0.22.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d249d6482ca9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.