# Issue

**Title:** Bump snakemake from 7.30.1 to 7.30.2

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.30.1 to 7.30.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.30.2</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.30.1...v7.30.2">7.30.2</a> (2023-07-20)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>do not allow setting benchmark and between-workflow caching for the same rule. The reason is that when the result is taken from cache, there is no way to fill the benchmark file with any reasonable values. (<a href="">#2335</a>) (<a href="">e2d64fa</a>)</li>
<li>ensure lazy evaluation of resource functions/callables (this also entails, for now, a removal of the thread statistics in the yellow job stats table); further, added some clarifying sentences about resource function evaluation to the docs (<a href="">#2356</a>) (<a href="">4c591b7</a>)</li>
<li>handle non-PEP440 versions of apptainer/singulariy (<a href="">#2337</a>) (<a href="">dea6ba8</a>)</li>
<li>remote GS builds too many inventories; io:collect_mtime always uses uncached mtime (<a href="">#2266</a>) (<a href="">bad9115</a>)</li>
<li>Solve apptainer version issue (<a href="">#2333</a>) (<a href="">a876e0f</a>)</li>
<li>SyntaxWarnings due to non-raw regex pattern strings (<a href="">#2359</a>) (<a href="">a08c0b0</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>clarify minimum Snakemake version for profiles (<a href="">86dc277</a>)</li>
<li>clarify the channel priority in environment definition deployment.rst (<a href="">#2352</a>) (<a href="">76aa964</a>)</li>
<li>fix typo (stackoverflow issue) (<a href="">#2365</a>) (<a href="">f770984</a>)</li>
<li>note on using checkpoint mechanism only for input function, not for params or resources. (<a href="">#2353</a>) (<a href="">4be2f9d</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.30.1...v7.30.2">7.30.2</a> (2023-07-20)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>do not allow setting benchmark and between-workflow caching for the same rule. The reason is that when the result is taken from cache, there is no way to fill the benchmark file with any reasonable values. (<a href="">#2335</a>) (<a href="">e2d64fa</a>)</li>
<li>ensure lazy evaluation of resource functions/callables (this also entails, for now, a removal of the thread statistics in the yellow job stats table); further, added some clarifying sentences about resource function evaluation to the docs (<a href="">#2356</a>) (<a href="">4c591b7</a>)</li>
<li>handle non-PEP440 versions of apptainer/singulariy (<a href="">#2337</a>) (<a href="">dea6ba8</a>)</li>
<li>remote GS builds too many inventories; io:collect_mtime always uses uncached mtime (<a href="">#2266</a>) (<a href="">bad9115</a>)</li>
<li>Solve apptainer version issue (<a href="">#2333</a>) (<a href="">a876e0f</a>)</li>
<li>SyntaxWarnings due to non-raw regex pattern strings (<a href="">#2359</a>) (<a href="">a08c0b0</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>clarify minimum Snakemake version for profiles (<a href="">86dc277</a>)</li>
<li>clarify the channel priority in environment definition deployment.rst (<a href="">#2352</a>) (<a href="">76aa964</a>)</li>
<li>fix typo (stackoverflow issue) (<a href="">#2365</a>) (<a href="">f770984</a>)</li>
<li>note on using checkpoint mechanism only for input function, not for params or resources. (<a href="">#2353</a>) (<a href="">4be2f9d</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9cfcd91</code></a> chore(main): release 7.30.2 (<a href="">#2338</a>)</li>
<li><a href=""><code>4c591b7</code></a> fix: ensure lazy evaluation of resource functions/callables (this also entail...</li>
<li><a href=""><code>f770984</code></a> docs: fix typo (stackoverflow issue) (<a href="">#2365</a>)</li>
<li><a href=""><code>a08c0b0</code></a> fix: SyntaxWarnings due to non-raw regex pattern strings (<a href="">#2359</a>)</li>
<li><a href=""><code>4be2f9d</code></a> docs: note on using checkpoint mechanism only for input function, not for par...</li>
<li><a href=""><code>76aa964</code></a> docs: clarify the channel priority in environment definition deployment.rst (...</li>
<li><a href=""><code>e9f6731</code></a> refactor: define consistent abstract base classes for jobs (<a href="">#2341</a>)</li>
<li><a href=""><code>86dc277</code></a> docs: clarify minimum Snakemake version for profiles</li>
<li><a href=""><code>bad9115</code></a> fix: remote GS builds too many inventories; io:collect_mtime always uses unca...</li>
<li><a href=""><code>e2d64fa</code></a> fix: do not allow setting benchmark and between-workflow caching for the same...</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.30.1...v7.30.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.30.1&new-version=7.30.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ede1b78273c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.