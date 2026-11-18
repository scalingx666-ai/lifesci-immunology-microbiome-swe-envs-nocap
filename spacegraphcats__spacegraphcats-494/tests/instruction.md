# Issue

**Title:** Bump snakemake from 7.24.2 to 7.25.0

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.24.2 to 7.25.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.25.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.24.2...v7.25.0">7.25.0</a> (2023-03-23)</h2>
<h3>Features</h3>
<ul>
<li>added localrule directive (<a href="">#2180</a>) (<a href="">9c990b0</a>)</li>
<li>Tes auth (<a href="">#2169</a>) (<a href="">3326a6f</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>always make sure that the original path of source cached files is properly passed into metadata persistence records (<a href="">#2179</a>) (<a href="">8bacbd0</a>)</li>
<li>slurm batch job status queries (<a href="">#2167</a>) (<a href="">0bb69e4</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Change snakemake-tutorial download link to always be the latest (<a href="">#2183</a>) (<a href="">ae8a8f4</a>)</li>
<li>fix typos in --help (<a href="">#2182</a>) (<a href="">09f0cbe</a>)</li>
<li>Improve error message when rule contains multiple run/shell/script/notebook/wrapper/template_engine/cwl keywords (<a href="">#2186</a>) (<a href="">cd5a3c4</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.24.2...v7.25.0">7.25.0</a> (2023-03-23)</h2>
<h3>Features</h3>
<ul>
<li>added localrule directive (<a href="">#2180</a>) (<a href="">9c990b0</a>)</li>
<li>Tes auth (<a href="">#2169</a>) (<a href="">3326a6f</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>always make sure that the original path of source cached files is properly passed into metadata persistence records (<a href="">#2179</a>) (<a href="">8bacbd0</a>)</li>
<li>slurm batch job status queries (<a href="">#2167</a>) (<a href="">0bb69e4</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Change snakemake-tutorial download link to always be the latest (<a href="">#2183</a>) (<a href="">ae8a8f4</a>)</li>
<li>fix typos in --help (<a href="">#2182</a>) (<a href="">09f0cbe</a>)</li>
<li>Improve error message when rule contains multiple run/shell/script/notebook/wrapper/template_engine/cwl keywords (<a href="">#2186</a>) (<a href="">cd5a3c4</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5e5cb61</code></a> chore(main): release 7.25.0 (<a href="">#2187</a>)</li>
<li><a href=""><code>8bacbd0</code></a> fix: always make sure that the original path of source cached files is proper...</li>
<li><a href=""><code>3326a6f</code></a> feat: Tes auth (<a href="">#2169</a>)</li>
<li><a href=""><code>0bb69e4</code></a> fix: slurm batch job status queries (<a href="">#2167</a>)</li>
<li><a href=""><code>cd5a3c4</code></a> docs: Improve error message when rule contains multiple run/shell/script/note...</li>
<li><a href=""><code>09f0cbe</code></a> docs: fix typos in --help (<a href="">#2182</a>)</li>
<li><a href=""><code>9c990b0</code></a> feat: added localrule directive (<a href="">#2180</a>)</li>
<li><a href=""><code>ae8a8f4</code></a> docs: Change snakemake-tutorial download link to always be the latest (<a href="">#2183</a>)</li>
<li><a href=""><code>2558ea5</code></a> chore: fix CI failures (<a href="">#2177</a>)</li>
<li>See full diff in <a href="https://github.com/snakemake/snakemake/compare/v7.24.2...v7.25.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.24.2&new-version=7.25.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ba7e0753a84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.