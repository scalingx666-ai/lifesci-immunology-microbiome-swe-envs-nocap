# Issue

**Title:** Bump snakemake from 9.4.0 to 9.5.1

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 9.4.0 to 9.5.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v9.5.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.5.0...v9.5.1">9.5.1</a> (2025-05-23)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>format output files in job cleanup message such that their remote query is shown instead of the local copy (<a href="">#3600</a>) (<a href="">91cc3ef</a>)</li>
<li>skip unnecessary schema validation inside of remote jobs (<a href="">#3601</a>) (<a href="">9129654</a>)</li>
</ul>
<h2>v9.5.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.4.1...v9.5.0">9.5.0</a> (2025-05-22)</h2>
<h3>Features</h3>
<ul>
<li>wildcards/callable function for container url (<a href="">#3590</a>) (<a href="">86733ee</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>fix errors with --list-changes (async generator error and --list-changes params yielding spurious files) (<a href="">#3598</a>) (<a href="">1c95cfa</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix typo when generating DAG (<a href="">#3568</a>) (<a href="">4f3d609</a>)</li>
</ul>
<h2>v9.4.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.4.0...v9.4.1">9.4.1</a> (2025-05-21)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>fix a typo in the docs:<code>nescessay</code> (<a href="">#3578</a>) (<a href="">b6961fd</a>)</li>
<li>fix spurious errors about external but returning dependencies in group jobs (<a href="">#3593</a>) (<a href="">1f7e254</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix syntax highlighting for light and dark theme (<a href="">9c5c6f7</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.5.0...v9.5.1">9.5.1</a> (2025-05-23)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>format output files in job cleanup message such that their remote query is shown instead of the local copy (<a href="">#3600</a>) (<a href="">91cc3ef</a>)</li>
<li>skip unnecessary schema validation inside of remote jobs (<a href="">#3601</a>) (<a href="">9129654</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.4.1...v9.5.0">9.5.0</a> (2025-05-22)</h2>
<h3>Features</h3>
<ul>
<li>wildcards/callable function for container url (<a href="">#3590</a>) (<a href="">86733ee</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>fix errors with --list-changes (async generator error and --list-changes params yielding spurious files) (<a href="">#3598</a>) (<a href="">1c95cfa</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix typo when generating DAG (<a href="">#3568</a>) (<a href="">4f3d609</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.4.0...v9.4.1">9.4.1</a> (2025-05-21)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>fix a typo in the docs:<code>nescessay</code> (<a href="">#3578</a>) (<a href="">b6961fd</a>)</li>
<li>fix spurious errors about external but returning dependencies in group jobs (<a href="">#3593</a>) (<a href="">1f7e254</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>fix syntax highlighting for light and dark theme (<a href="">9c5c6f7</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5f04aea</code></a> chore(main): release 9.5.1 (<a href="">#3603</a>)</li>
<li><a href=""><code>91cc3ef</code></a> fix: format output files in job cleanup message such that their remote query ...</li>
<li><a href=""><code>9129654</code></a> fix: skip unnecessary schema validation inside of remote jobs (<a href="">#3601</a>)</li>
<li><a href=""><code>65a5360</code></a> chore(main): release 9.5.0 (<a href="">#3595</a>)</li>
<li><a href=""><code>1c95cfa</code></a> fix: fix errors with --list-changes (async generator error and --list-changes...</li>
<li><a href=""><code>86733ee</code></a> feat: wildcards/callable function for container url (<a href="">#3590</a>)</li>
<li><a href=""><code>4f3d609</code></a> docs: Fix typo when generating DAG (<a href="">#3568</a>)</li>
<li><a href=""><code>a767448</code></a> chore(main): release 9.4.1 (<a href="">#3577</a>)</li>
<li><a href=""><code>3291f9b</code></a> chore: use pixi build environment on release (<a href="">#3581</a>)</li>
<li><a href=""><code>1f7e254</code></a> fix: fix spurious errors about external but returning dependencies in group j...</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v9.4.0...v9.5.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=9.4.0&new-version=9.5.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92b265632749`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.