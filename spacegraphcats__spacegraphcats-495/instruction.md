# Issue

**Title:** Bump snakemake from 7.25.0 to 7.25.2

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.25.0 to 7.25.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.25.2</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.25.1...v7.25.2">7.25.2</a> (2023-04-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Fix inconsistencies between detailed summary and normal summary (<a href="">#2218</a>) (<a href="">d903123</a>)</li>
<li>Fix race condition when creating lock directory (<a href="">#2225</a>) (<a href="">66ea4d1</a>)</li>
<li>quote paths given to singularity in order to ensure that it does not fail when paths contain whitespace (<a href="">#2190</a>) (<a href="">a572fb7</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>added changelog info for &gt;v7.19.1 parsing error of &quot;hh:mm:ss&quot; time format in runtime resource (<a href="">#2189</a>) (<a href="">2889f38</a>)</li>
<li>update misc/vim/Readme with info for packer.nvim (<a href="">#2095</a>) (<a href="">32166a7</a>)</li>
<li>Update workflow syntax with priority directive (<a href="">#2188</a>) (<a href="">af10db5</a>)</li>
</ul>
<h2>v7.25.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.25.0...v7.25.1">7.25.1</a> (2023-04-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>allow log directive in default target rule (<a href="">#2191</a>) (<a href="">86e9624</a>)</li>
<li>only consider global wildcard_constraints from the same module (<a href="">#2235</a>) (<a href="">c412b71</a>)</li>
<li>Use <code>job.rule.name</code> attribute to fill rule field in summary (<a href="">#2217</a>) (<a href="">837c3fd</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix formatting (<a href="">087fe63</a>)</li>
<li>replace <code>nosetest</code> with <code>pytest</code> (<a href="">#2211</a>) (<a href="">f6b3c47</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.25.1...v7.25.2">7.25.2</a> (2023-04-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Fix inconsistencies between detailed summary and normal summary (<a href="">#2218</a>) (<a href="">d903123</a>)</li>
<li>Fix race condition when creating lock directory (<a href="">#2225</a>) (<a href="">66ea4d1</a>)</li>
<li>quote paths given to singularity in order to ensure that it does not fail when paths contain whitespace (<a href="">#2190</a>) (<a href="">a572fb7</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>added changelog info for &gt;v7.19.1 parsing error of &quot;hh:mm:ss&quot; time format in runtime resource (<a href="">#2189</a>) (<a href="">2889f38</a>)</li>
<li>update misc/vim/Readme with info for packer.nvim (<a href="">#2095</a>) (<a href="">32166a7</a>)</li>
<li>Update workflow syntax with priority directive (<a href="">#2188</a>) (<a href="">af10db5</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.25.0...v7.25.1">7.25.1</a> (2023-04-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>allow log directive in default target rule (<a href="">#2191</a>) (<a href="">86e9624</a>)</li>
<li>only consider global wildcard_constraints from the same module (<a href="">#2235</a>) (<a href="">c412b71</a>)</li>
<li>Use <code>job.rule.name</code> attribute to fill rule field in summary (<a href="">#2217</a>) (<a href="">837c3fd</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix formatting (<a href="">087fe63</a>)</li>
<li>replace <code>nosetest</code> with <code>pytest</code> (<a href="">#2211</a>) (<a href="">f6b3c47</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c7ae161</code></a> chore(main): release 7.25.2 (<a href="">#2237</a>)</li>
<li><a href=""><code>32166a7</code></a> docs: update misc/vim/Readme with info for packer.nvim (<a href="">#2095</a>)</li>
<li><a href=""><code>af10db5</code></a> docs: Update workflow syntax with priority directive (<a href="">#2188</a>)</li>
<li><a href=""><code>2889f38</code></a> docs: added changelog info for &gt;v7.19.1 parsing error of &quot;hh:mm:ss&quot; time form...</li>
<li><a href=""><code>a572fb7</code></a> fix: quote paths given to singularity in order to ensure that it does not fai...</li>
<li><a href=""><code>d903123</code></a> fix: Fix inconsistencies between detailed summary and normal summary (<a href="">#2218</a>)</li>
<li><a href=""><code>66ea4d1</code></a> fix: Fix race condition when creating lock directory (<a href="">#2225</a>)</li>
<li><a href=""><code>da246d2</code></a> chore(main): release 7.25.1 (<a href="">#2226</a>)</li>
<li><a href=""><code>4ddc644</code></a> chore(deps): Bump marocchino/sticky-pull-request-comment from 2.5.0 to 2.6.2 ...</li>
<li><a href=""><code>837c3fd</code></a> fix: Use <code>job.rule.name</code> attribute to fill rule field in summary (<a href="">#2217</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.25.0...v7.25.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.25.0&new-version=7.25.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2dde99d8b503`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.