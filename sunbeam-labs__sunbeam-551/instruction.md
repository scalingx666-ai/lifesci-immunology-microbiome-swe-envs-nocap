# Issue

**Title:** Bump snakemake from 9.8.2 to 9.9.0

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 9.8.2 to 9.9.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v9.9.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.8.2...v9.9.0">9.9.0</a> (2025-07-29)</h2>
<h3>Features</h3>
<ul>
<li>python 3.13 support (<a href="">#3602</a>) (<a href="">429cff4</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>dag mermaid-js edges (bug:<a href="">#3556</a>) (<a href="">#3669</a>) (<a href="">c6e2e71</a>)</li>
<li>if asset is present and no sha256 provided assume pass (<a href="">#3685</a>) (<a href="">7731175</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v9.8.2...v9.9.0">9.9.0</a> (2025-07-29)</h2>
<h3>Features</h3>
<ul>
<li>python 3.13 support (<a href="">#3602</a>) (<a href="">429cff4</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>dag mermaid-js edges (bug:<a href="">#3556</a>) (<a href="">#3669</a>) (<a href="">c6e2e71</a>)</li>
<li>if asset is present and no sha256 provided assume pass (<a href="">#3685</a>) (<a href="">7731175</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ea7bdb2</code></a> chore(main): release 9.9.0 (<a href="">#3683</a>)</li>
<li><a href=""><code>43d1442</code></a> build(deps): bump prefix-dev/setup-pixi from 0.8.11 to 0.8.14 (<a href="">#3686</a>)</li>
<li><a href=""><code>c6e2e71</code></a> fix: dag mermaid-js edges (bug:<a href="">#3556</a>) (<a href="">#3669</a>)</li>
<li><a href=""><code>7731175</code></a> fix: if asset is present and no sha256 provided assume pass (<a href="">#3685</a>)</li>
<li><a href=""><code>429cff4</code></a> feat: python 3.13 support (<a href="">#3602</a>)</li>
<li>See full diff in <a href="https://github.com/snakemake/snakemake/compare/v9.8.2...v9.9.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=9.8.2&new-version=9.9.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f5d6ce4e019`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.