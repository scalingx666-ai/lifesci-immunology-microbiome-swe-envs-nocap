# Issue

**Title:** Bump snakemake from 7.24.0 to 7.24.2

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.24.0 to 7.24.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.24.2</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.24.1...v7.24.2">7.24.2</a> (2023-03-14)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>fix index out of bounds error raised by usage of workflow.source_path called from input or params functions (thanks <a href="https://github.com/AKBrueggemann"><code>@​AKBrueggemann</code></a>) (<a href="">#2170</a>) (<a href="">cf8e6e8</a>)</li>
<li>limit length of failed logs decorations (<a href="">#2125</a>) (<a href="">6fc9243</a>)</li>
<li>raise error if callable is passed to expand. (<a href="">#2171</a>) (<a href="">1f28476</a>)</li>
<li>rounding for batch calculation (<a href="">#2064</a>) (<a href="">cbdbf9b</a>)</li>
</ul>
<h2>v7.24.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.24.0...v7.24.1">7.24.1</a> (2023-03-09)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>better job status queries for slurm executor  (<a href="">#2136</a>) (<a href="">a4df38c</a>)</li>
<li>get python version for script environment in a backwards compatible way that works down to python 2.7 (<a href="">#2161</a>) (<a href="">44e59b9</a>)</li>
<li>prevents DeprecationWarning caused by using old  draft of json schema (<a href="">#2152</a>) (<a href="">9791ffb</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>Gfal2 remote provider using gfal2-python instead of  gfal2-utils. (<a href="">#2128</a>) (<a href="">0b9bfe5</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix minor typos in a linting rule (<a href="">#2162</a>) (<a href="">71e1171</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.24.1...v7.24.2">7.24.2</a> (2023-03-14)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>fix index out of bounds error raised by usage of workflow.source_path called from input or params functions (thanks <a href="https://github.com/AKBrueggemann"><code>@​AKBrueggemann</code></a>) (<a href="">#2170</a>) (<a href="">cf8e6e8</a>)</li>
<li>limit length of failed logs decorations (<a href="">#2125</a>) (<a href="">6fc9243</a>)</li>
<li>raise error if callable is passed to expand. (<a href="">#2171</a>) (<a href="">1f28476</a>)</li>
<li>rounding for batch calculation (<a href="">#2064</a>) (<a href="">cbdbf9b</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.24.0...v7.24.1">7.24.1</a> (2023-03-09)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>better job status queries for slurm executor  (<a href="">#2136</a>) (<a href="">a4df38c</a>)</li>
<li>get python version for script environment in a backwards compatible way that works down to python 2.7 (<a href="">#2161</a>) (<a href="">44e59b9</a>)</li>
<li>prevents DeprecationWarning caused by using old  draft of json schema (<a href="">#2152</a>) (<a href="">9791ffb</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>Gfal2 remote provider using gfal2-python instead of  gfal2-utils. (<a href="">#2128</a>) (<a href="">0b9bfe5</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix minor typos in a linting rule (<a href="">#2162</a>) (<a href="">71e1171</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1fb3cef</code></a> chore(main): release 7.24.2 (<a href="">#2172</a>)</li>
<li><a href=""><code>1f28476</code></a> fix: raise error if callable is passed to expand. (<a href="">#2171</a>)</li>
<li><a href=""><code>cf8e6e8</code></a> fix: fix index out of bounds error raised by usage of workflow.source_path ca...</li>
<li><a href=""><code>cbdbf9b</code></a> fix: rounding for batch calculation (<a href="">#2064</a>)</li>
<li><a href=""><code>6fc9243</code></a> fix: limit length of failed logs decorations (<a href="">#2125</a>)</li>
<li><a href=""><code>24ca47e</code></a> also mimic account query</li>
<li><a href=""><code>000c6d4</code></a> provide proxy command for sacct in CI</li>
<li><a href=""><code>6c26980</code></a> chore(main): release 7.24.1 (<a href="">#2157</a>)</li>
<li><a href=""><code>0b9bfe5</code></a> perf: Gfal2 remote provider using gfal2-python instead of  gfal2-utils. (<a href="">#2128</a>)</li>
<li><a href=""><code>9791ffb</code></a> fix: prevents DeprecationWarning caused by using old  draft of json schema (#...</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.24.0...v7.24.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.24.0&new-version=7.24.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `655a69ff6776`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.