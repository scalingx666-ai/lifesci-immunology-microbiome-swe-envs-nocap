# Issue

**Title:** Bump snakemake from 9.7.1 to 9.8.2

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 9.7.1 to 9.8.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v9.8.2</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.8.1...v9.8.2">9.8.2</a> (2025-07-25)</h2>
<h3>Documentation</h3>
<ul>
<li>info about snakedeploy (<a href="">#3681</a>) (<a href="">6ff65ae</a>)</li>
</ul>
<h2>v9.8.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.8.0...v9.8.1">9.8.1</a> (2025-07-21)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>pass kwargs to StorageRegistry call (<a href="">#3631</a>) (<a href="">2c35e76</a>)</li>
</ul>
<h2>v9.8.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.7.1...v9.8.0">9.8.0</a> (2025-07-10)</h2>
<h3>Features</h3>
<ul>
<li>add <code>--no-temp</code> flag synonymous to <code>--notemp</code> (<a href="">#3632</a>) (<a href="">c775634</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>fix exception when joining rule basedir to script or conda env path (<a href="">#3668</a>) (<a href="">347420c</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Update pixi setup section of tutorial (<a href="">#3664</a>) (<a href="">104203b</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.8.1...v9.8.2">9.8.2</a> (2025-07-25)</h2>
<h3>Documentation</h3>
<ul>
<li>info about snakedeploy (<a href="">#3681</a>) (<a href="">6ff65ae</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.8.0...v9.8.1">9.8.1</a> (2025-07-21)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>pass kwargs to StorageRegistry call (<a href="">#3631</a>) (<a href="">2c35e76</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.7.1...v9.8.0">9.8.0</a> (2025-07-10)</h2>
<h3>Features</h3>
<ul>
<li>add <code>--no-temp</code> flag synonymous to <code>--notemp</code> (<a href="">#3632</a>) (<a href="">c775634</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>fix exception when joining rule basedir to script or conda env path (<a href="">#3668</a>) (<a href="">347420c</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Update pixi setup section of tutorial (<a href="">#3664</a>) (<a href="">104203b</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ead3f0a</code></a> chore(main): release 9.8.2 (<a href="">#3682</a>)</li>
<li><a href=""><code>6ff65ae</code></a> docs: info about snakedeploy (<a href="">#3681</a>)</li>
<li><a href=""><code>b88259e</code></a> chore(main): release 9.8.1 (<a href="">#3674</a>)</li>
<li><a href=""><code>0327915</code></a> build(deps): bump prefix-dev/setup-pixi from 0.8.8 to 0.8.11 (<a href="">#3673</a>)</li>
<li><a href=""><code>2c35e76</code></a> fix: pass kwargs to StorageRegistry call (<a href="">#3631</a>)</li>
<li><a href=""><code>7f2606e</code></a> chore(main): release 9.8.0 (<a href="">#3662</a>)</li>
<li><a href=""><code>104203b</code></a> docs: Update pixi setup section of tutorial (<a href="">#3664</a>)</li>
<li><a href=""><code>347420c</code></a> fix: fix exception when joining rule basedir to script or conda env path (<a href="">#3668</a>)</li>
<li><a href=""><code>c775634</code></a> feat: add <code>--no-temp</code> flag synonymous to <code>--notemp</code> (<a href="">#3632</a>)</li>
<li>See full diff in <a href="https://github.com/snakemake/snakemake/compare/v9.7.1...v9.8.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=9.7.1&new-version=9.8.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cb1210519a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.