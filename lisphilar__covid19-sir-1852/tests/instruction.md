# Issue

**Title:** build(deps-dev): bump deptry from 0.23.0 to 0.23.1

## Description

Bumps [deptry](https://github.com/fpgmaas/deptry) from 0.23.0 to 0.23.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/releases">deptry's releases</a>.</em></p>
<blockquote>
<h2>0.23.1</h2>
<h2>What's Changed</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Improve handling of <code>TYPE_CHECKING</code> blocks by supporting <code>import typing as t</code> and checking <code>t.TYPE_CHECKING</code> (<a href="">#1218</a>)</li>
<li>Fix missing hyperlink in report output (<a href="">#1162</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.23.0...0.23.1">https://github.com/fpgmaas/deptry/compare/0.23.0...0.23.1</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/blob/main/CHANGELOG.md">deptry's changelog</a>.</em></p>
<blockquote>
<h2>0.23.1 - 2025-07-30</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Improve handling of <code>TYPE_CHECKING</code> blocks by supporting <code>import typing as t</code> and checking <code>t.TYPE_CHECKING</code> (<a href="">#1218</a>)</li>
<li>Fix missing hyperlink in report output (<a href="">#1162</a>)</li>
</ul>
<h3>Full Changelog</h3>
<p><a href="https://github.com/fpgmaas/deptry/compare/0.23.0...0.23.1">https://github.com/fpgmaas/deptry/compare/0.23.0...0.23.1</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>709204b</code></a> Changelog for 0.23.1 (<a href="">#1226</a>)</li>
<li><a href=""><code>0684ec0</code></a> allow typing alias for TYPE_CHECKING (<a href="">#1218</a>)</li>
<li><a href=""><code>d6682ab</code></a> chore(deps): lock file maintenance (<a href="">#1223</a>)</li>
<li><a href=""><code>840d5fb</code></a> chore(deps): update uv-version to v0.8.3 (<a href="">#1221</a>)</li>
<li><a href=""><code>608161f</code></a> test: update dependencies in tests to v4.25.0.20250720 (<a href="">#1222</a>)</li>
<li><a href=""><code>71ec469</code></a> chore(deps): update astral-sh/setup-uv action to v6.4.3 (<a href="">#1219</a>)</li>
<li><a href=""><code>4fed1ad</code></a> chore(deps): update pre-commit hook astral-sh/ruff-pre-commit to v0.12.5 (<a href="">#1220</a>)</li>
<li><a href=""><code>775e6bc</code></a> chore(deps): lock file maintenance (<a href="">#1216</a>)</li>
<li><a href=""><code>7b212fc</code></a> chore: bump Ruff parser to 0.12.4 (<a href="">#1217</a>)</li>
<li><a href=""><code>730d1fd</code></a> chore(deps): update uv-version to v0.8.0 (<a href="">#1215</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/fpgmaas/deptry/compare/0.23.0...0.23.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=deptry&package-manager=pip&previous-version=0.23.0&new-version=0.23.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc0e290869b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.