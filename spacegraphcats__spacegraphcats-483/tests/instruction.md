# Issue

**Title:** Bump snakemake from 7.18.2 to 7.19.0

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.18.2 to 7.19.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.19.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.18.2...v7.19.0">7.19.0</a> (2022-12-13)</h2>
<h3>Features</h3>
<ul>
<li>add  keyword to gridftp remote provide to specify the number or disable usage of multiple data stream (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1974">#1974</a>) (<a href="">3e6675d</a>)</li>
<li>provide information about temp, pipe, and service files in --summary (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1977">#1977</a>) (<a href="">c7c7776</a>)</li>
<li>native SLURM support (--slurm, see docs) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1015">#1015</a>) (<a href="">c7ea059</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>avoid logfile writing in case of dryrun; better hints in case of incomplete checkpoints (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1994">#1994</a>) (<a href="">a022705</a>)</li>
<li>handle case where zenodo deposition does not return files (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2004">#2004</a>) (<a href="">b63c4a7</a>)</li>
<li>issue <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1882">#1882</a> WorkflowError: Metadata can't be created as it already exists (Windows) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1971">#1971</a>) (<a href="">d4484e6</a>)</li>
<li>json validation error with markdown cells (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1986">#1986</a>) (<a href="">6c26f75</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.18.2...v7.19.0">7.19.0</a> (2022-12-13)</h2>
<h3>Features</h3>
<ul>
<li>add  keyword to gridftp remote provide to specify the number or disable usage of multiple data stream (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1974">#1974</a>) (<a href="">3e6675d</a>)</li>
<li>provide information about temp, pipe, and service files in --summary (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1977">#1977</a>) (<a href="">c7c7776</a>)</li>
<li>native SLURM support (--slurm, see docs) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1015">#1015</a>) (<a href="">c7ea059</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>avoid logfile writing in case of dryrun; better hints in case of incomplete checkpoints (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1994">#1994</a>) (<a href="">a022705</a>)</li>
<li>handle case where zenodo deposition does not return files (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2004">#2004</a>) (<a href="">b63c4a7</a>)</li>
<li>issue <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1882">#1882</a> WorkflowError: Metadata can't be created as it already exists (Windows) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1971">#1971</a>) (<a href="">d4484e6</a>)</li>
<li>json validation error with markdown cells (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1986">#1986</a>) (<a href="">6c26f75</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>88d9268</code></a> chore(main): release 7.19.0 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1995">#1995</a>)</li>
<li><a href=""><code>c7ea059</code></a> feat: SLURM executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1015">#1015</a>)</li>
<li><a href=""><code>b63c4a7</code></a> fix: handle case where zenodo deposition does not return files (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2004">#2004</a>)</li>
<li><a href=""><code>a022705</code></a> fix: avoid logfile writing in case of dryrun; better hints in case of incompl...</li>
<li><a href=""><code>d4484e6</code></a> fix: issue <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1882">#1882</a> WorkflowError: Metadata can't be created as it already exist...</li>
<li><a href=""><code>3e6675d</code></a> feat: add  keyword to gridftp remote provide to specify the number or disable...</li>
<li><a href=""><code>c7c7776</code></a> feat: provide information about temp, pipe, and service files in --summary (#...</li>
<li><a href=""><code>6c26f75</code></a> fix: json validation error with markdown cells (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1986">#1986</a>)</li>
<li><a href=""><code>7331bb1</code></a> chore: remove slurm setup and wait for PR <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1015">#1015</a></li>
<li>See full diff in <a href="https://github.com/snakemake/snakemake/compare/v7.18.2...v7.19.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.18.2&new-version=7.19.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc839d0f5cfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.