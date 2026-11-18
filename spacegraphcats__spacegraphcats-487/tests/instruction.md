# Issue

**Title:** Bump snakemake from 7.20.0 to 7.21.0

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.20.0 to 7.21.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.21.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.20.0...v7.21.0">7.21.0</a> (2023-01-30)</h2>
<h3>Features</h3>
<ul>
<li>ability to encode paramspaces into a single wildcard, via the newly introduced <code>single_wildcard</code> argument of <code>Paramspace</code>. (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2069">#2069</a>) (<a href="">728ab3c</a>)</li>
<li>allow input, output, and params to be used in functions passed to report mark arguments (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2081">#2081</a>) (<a href="">93ff8b6</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>more robust encoding of params in persistent metadata storage. This way, pandas parameters do not lead to spurious rerun triggers. (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2080">#2080</a>) (<a href="">106a4c3</a>)</li>
<li>more robust parsing of sacct output in slurm executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2036">#2036</a>) (<a href="">fe651f8</a>)</li>
<li>Postprocess job groups in toposorted order for correct touch times (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2073">#2073</a>) (<a href="">10b5849</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.20.0...v7.21.0">7.21.0</a> (2023-01-30)</h2>
<h3>Features</h3>
<ul>
<li>ability to encode paramspaces into a single wildcard, via the newly introduced <code>single_wildcard</code> argument of <code>Paramspace</code>. (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2069">#2069</a>) (<a href="">728ab3c</a>)</li>
<li>allow input, output, and params to be used in functions passed to report mark arguments (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2081">#2081</a>) (<a href="">93ff8b6</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>more robust encoding of params in persistent metadata storage. This way, pandas parameters do not lead to spurious rerun triggers. (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2080">#2080</a>) (<a href="">106a4c3</a>)</li>
<li>more robust parsing of sacct output in slurm executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2036">#2036</a>) (<a href="">fe651f8</a>)</li>
<li>Postprocess job groups in toposorted order for correct touch times (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2073">#2073</a>) (<a href="">10b5849</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8f79f22</code></a> chore(main): release 7.21.0 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2074">#2074</a>)</li>
<li><a href=""><code>93ff8b6</code></a> feat:  allow input, output, and params to be used in functions passed to repo...</li>
<li><a href=""><code>106a4c3</code></a> fix: more robust encoding of params in persistent metadata storage. This way,...</li>
<li><a href=""><code>ac83023</code></a> chore(deps): Bump amannn/action-semantic-pull-request from 4.6.0 to 5.0.2 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1">#1</a>...</li>
<li><a href=""><code>fe651f8</code></a> fix: more robust parsing of sacct output in slurm executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2036">#2036</a>)</li>
<li><a href=""><code>10b5849</code></a> fix: Postprocess job groups in toposorted order for correct touch times (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2073">#2073</a>)</li>
<li><a href=""><code>728ab3c</code></a> feat: ability to encode paramspaces into a single wildcard, via the newly int...</li>
<li>See full diff in <a href="https://github.com/snakemake/snakemake/compare/v7.20.0...v7.21.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.20.0&new-version=7.21.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1018b3ce6aa3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.