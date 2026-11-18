# Issue

**Title:** Bump snakemake from 7.25.2 to 7.30.1

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.25.2 to 7.30.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.30.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.30.0...v7.30.1">7.30.1</a> (2023-06-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>conda env inside script (<a href="">#1812</a>) (<a href="">49cac6a</a>)</li>
</ul>
<h2>v7.30.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.29.0...v7.30.0">7.30.0</a> (2023-06-28)</h2>
<h3>Features</h3>
<ul>
<li>allow profiles to be YTE templates; adapt to eido 2.0 (<a href="">#2325</a>) (<a href="">67d9ff2</a>)</li>
</ul>
<h2>v7.29.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.28.3...v7.29.0">7.29.0</a> (2023-06-21)</h2>
<h3>Features</h3>
<ul>
<li>introduce --workflow-profile for additional workflow specific profiles that overwrite global profiles; add ability to define key-value CLI flags like --set-threads or --set-resources as multi-level dictionaries in profile config yaml files (<a href="">#2310</a>) (<a href="">9675c17</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>addressing <a href="">#2197</a> by allowing 256 character account names in slurm (<a href="">#2198</a>) (<a href="">ab58c65</a>)</li>
<li>removed distutils from snakemake (<a href="">#2312</a>) (<a href="">9b8c362</a>)</li>
<li>Update <strong>init</strong>.py to move &quot;file&quot; param to &quot;print&quot; (<a href="">#2291</a>) (<a href="">92352b6</a>)</li>
</ul>
<h2>v7.28.3</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.28.2...v7.28.3">7.28.3</a> (2023-06-16)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Detect pandas availability to select serializer (<a href="">#2300</a>) (<a href="">e08a771</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>avoid superflous mtime checks when the same file is referred to by multiple jobs (<a href="">#2284</a>) (<a href="">eb6e2e1</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>update docs for azbatch and dockerhub ref (<a href="">#2298</a>) (<a href="">908dbf1</a>)</li>
</ul>
<h2>v7.28.2</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.30.0...v7.30.1">7.30.1</a> (2023-06-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>conda env inside script (<a href="">#1812</a>) (<a href="">49cac6a</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.29.0...v7.30.0">7.30.0</a> (2023-06-28)</h2>
<h3>Features</h3>
<ul>
<li>allow profiles to be YTE templates; adapt to eido 2.0 (<a href="">#2325</a>) (<a href="">67d9ff2</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.28.3...v7.29.0">7.29.0</a> (2023-06-21)</h2>
<h3>Features</h3>
<ul>
<li>introduce --workflow-profile for additional workflow specific profiles that overwrite global profiles; add ability to define key-value CLI flags like --set-threads or --set-resources as multi-level dictionaries in profile config yaml files (<a href="">#2310</a>) (<a href="">9675c17</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>addressing <a href="">#2197</a> by allowing 256 character account names in slurm (<a href="">#2198</a>) (<a href="">ab58c65</a>)</li>
<li>removed distutils from snakemake (<a href="">#2312</a>) (<a href="">9b8c362</a>)</li>
<li>Update <strong>init</strong>.py to move &quot;file&quot; param to &quot;print&quot; (<a href="">#2291</a>) (<a href="">92352b6</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.28.2...v7.28.3">7.28.3</a> (2023-06-16)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Detect pandas availability to select serializer (<a href="">#2300</a>) (<a href="">e08a771</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>avoid superflous mtime checks when the same file is referred to by multiple jobs (<a href="">#2284</a>) (<a href="">eb6e2e1</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>update docs for azbatch and dockerhub ref (<a href="">#2298</a>) (<a href="">908dbf1</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.28.1...v7.28.2">7.28.2</a> (2023-06-13)</h2>
<h3>Bug Fixes</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>abb8410</code></a> chore(main): release 7.30.1 (<a href="">#2332</a>)</li>
<li><a href=""><code>49cac6a</code></a> fix: conda env inside script (<a href="">#1812</a>)</li>
<li><a href=""><code>27da95d</code></a> chore(main): release 7.30.0 (<a href="">#2329</a>)</li>
<li><a href=""><code>67d9ff2</code></a> feat: allow profiles to be YTE templates; adapt to eido 2.0 (<a href="">#2325</a>)</li>
<li><a href=""><code>f1b8342</code></a> chore(main): release 7.29.0 (<a href="">#2303</a>)</li>
<li><a href=""><code>9b8c362</code></a> fix: removed distutils from snakemake (<a href="">#2312</a>)</li>
<li><a href=""><code>9675c17</code></a> feat: introduce --workflow-profile for additional workflow specific profiles ...</li>
<li><a href=""><code>b561bde</code></a> refactor:  more format() and %s replaced by f-strings (<a href="">#2313</a>)</li>
<li><a href=""><code>4c34300</code></a> chore: fix conda custom prefix test on windows (<a href="">#2309</a>)</li>
<li><a href=""><code>ab58c65</code></a> fix: addressing <a href="">#2197</a> by allowing 256 character account names in slurm (<a href="">#2198</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.25.2...v7.30.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.25.2&new-version=7.30.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b79f25999a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.