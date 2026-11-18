# Issue

**Title:** Bump snakemake from 9.6.2 to 9.7.1

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 9.6.2 to 9.7.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v9.7.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.7.0...v9.7.1">9.7.1</a> (2025-07-04)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>cancel executor upon error during scheduling (<a href="">#3660</a>) (<a href="">d14a9bb</a>)</li>
</ul>
<h2>v9.7.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.6.3...v9.7.0">9.7.0</a> (2025-07-04)</h2>
<h3>Features</h3>
<ul>
<li>add --omit-flags for omitting flags in workflows; e.g. --omit-flags pipe treats output marked as pipe as normal output instead (<a href="">#3659</a>) (<a href="">b21dcf0</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>fix incomplete help text of --cache argument. (<a href="">#3279</a>) (<a href="">9ba6a9d</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix indentation (<a href="">35c6216</a>)</li>
</ul>
<h2>v9.6.3</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.6.2...v9.6.3">9.6.3</a> (2025-07-04)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>check protected files after DAG creation (<a href="">#3655</a>) (<a href="">882321b</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>refine default resources to provide more realistic estimates for most cases (<a href="">#3656</a>) (<a href="">5583c07</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>ensure that readthedocs ads do not hide the navigation sidebar (<a href="">#3652</a>) (<a href="">0b5f1d2</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.7.0...v9.7.1">9.7.1</a> (2025-07-04)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>cancel executor upon error during scheduling (<a href="">#3660</a>) (<a href="">d14a9bb</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.6.3...v9.7.0">9.7.0</a> (2025-07-04)</h2>
<h3>Features</h3>
<ul>
<li>add --omit-flags for omitting flags in workflows; e.g. --omit-flags pipe treats output marked as pipe as normal output instead (<a href="">#3659</a>) (<a href="">b21dcf0</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>fix incomplete help text of --cache argument. (<a href="">#3279</a>) (<a href="">9ba6a9d</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix indentation (<a href="">35c6216</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.6.2...v9.6.3">9.6.3</a> (2025-07-04)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>check protected files after DAG creation (<a href="">#3655</a>) (<a href="">882321b</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>refine default resources to provide more realistic estimates for most cases (<a href="">#3656</a>) (<a href="">5583c07</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>ensure that readthedocs ads do not hide the navigation sidebar (<a href="">#3652</a>) (<a href="">0b5f1d2</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c4a17a2</code></a> chore(main): release 9.7.1 (<a href="">#3661</a>)</li>
<li><a href=""><code>d14a9bb</code></a> fix: cancel executor upon error during scheduling (<a href="">#3660</a>)</li>
<li><a href=""><code>22d0023</code></a> chore(main): release 9.7.0 (<a href="">#3658</a>)</li>
<li><a href=""><code>b21dcf0</code></a> feat: add --omit-flags for omitting flags in workflows; e.g. --omit-flags pip...</li>
<li><a href=""><code>35c6216</code></a> docs: fix indentation</li>
<li><a href=""><code>9ba6a9d</code></a> fix: fix incomplete help text of --cache argument. (<a href="">#3279</a>)</li>
<li><a href=""><code>fd6b64f</code></a> chore(main): release 9.6.3 (<a href="">#3657</a>)</li>
<li><a href=""><code>f086581</code></a> refactor:  implement AnnotatedStringInterface from snakemake_interface_common...</li>
<li><a href=""><code>882321b</code></a> fix: check protected files after DAG creation (<a href="">#3655</a>)</li>
<li><a href=""><code>5583c07</code></a> perf: refine default resources to provide more realistic estimates for most c...</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v9.6.2...v9.7.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=9.6.2&new-version=9.7.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a7986893737`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.