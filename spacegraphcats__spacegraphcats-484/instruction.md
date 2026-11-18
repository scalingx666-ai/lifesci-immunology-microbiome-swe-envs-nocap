# Issue

**Title:** Bump snakemake from 7.19.0 to 7.19.1

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.19.0 to 7.19.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.19.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.19.0...v7.19.1">7.19.1</a> (2022-12-13)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>improved default resources parsing (also allowing to deactivate a default resource via setting it to None) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2006">#2006</a>) (<a href="">e6cdb32</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix link (<a href="">4889c93</a>)</li>
<li>fix typo (<a href="">e1c3cc6</a>)</li>
<li>fix typos (<a href="">e45b9e6</a>)</li>
<li>fix typos (<a href="">151095d</a>)</li>
<li>format table (<a href="">4180a1b</a>)</li>
<li>polished text and table display (<a href="">413356c</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.19.0...v7.19.1">7.19.1</a> (2022-12-13)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>improved default resources parsing (also allowing to deactivate a default resource via setting it to None) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2006">#2006</a>) (<a href="">e6cdb32</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix link (<a href="">4889c93</a>)</li>
<li>fix typo (<a href="">e1c3cc6</a>)</li>
<li>fix typos (<a href="">e45b9e6</a>)</li>
<li>fix typos (<a href="">151095d</a>)</li>
<li>format table (<a href="">4180a1b</a>)</li>
<li>polished text and table display (<a href="">413356c</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bd4505b</code></a> chore(main): release 7.19.1 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2005">#2005</a>)</li>
<li><a href=""><code>e6cdb32</code></a> fix: improved default resources parsing (also allowing to deactivate a defaul...</li>
<li><a href=""><code>413356c</code></a> docs: polished text and table display</li>
<li><a href=""><code>4180a1b</code></a> docs: format table</li>
<li><a href=""><code>e45b9e6</code></a> docs: fix typos</li>
<li><a href=""><code>e1c3cc6</code></a> docs: fix typo</li>
<li><a href=""><code>4889c93</code></a> docs: fix link</li>
<li><a href=""><code>151095d</code></a> docs: fix typos</li>
<li>See full diff in <a href="https://github.com/snakemake/snakemake/compare/v7.19.0...v7.19.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.19.0&new-version=7.19.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `406120cbc0e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.