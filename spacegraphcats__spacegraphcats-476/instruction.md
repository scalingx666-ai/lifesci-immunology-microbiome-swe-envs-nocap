# Issue

**Title:** Bump snakemake from 7.3.8 to 7.18.2

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.3.8 to 7.18.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.18.2</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.18.1...v7.18.2">7.18.2</a> (2022-11-10)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Change ratelimiter dependency to throttler (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1958">#1958</a>) (<a href="">50b8f16</a>)</li>
<li>fixed problem with leaked modifications when inheriting multiple times from the same rule (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1957">#1957</a>) (<a href="">2475cbc</a>)</li>
<li>forwarding --keep-incomplete to cluster executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1951">#1951</a>) (<a href="">2894c7d</a>)</li>
<li>show input files on job error (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1949">#1949</a>) (<a href="">ad21631</a>)</li>
</ul>
<h2>v7.18.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.18.0...v7.18.1">7.18.1</a> (2022-11-03)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>regression ValueError introduced with 7.17.2 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1947">#1947</a>) (<a href="">53a4fca</a>)</li>
</ul>
<h2>v7.18.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.17.2...v7.18.0">7.18.0</a> (2022-10-31)</h2>
<h3>Features</h3>
<ul>
<li>first try to match output files against input files while persisting wildcard values from the consuming job. This can dramatically reduce ambiuity problems. Thanks to <a href="https://github.com/descostesn"><code>@​descostesn</code></a>! (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1939">#1939</a>) (<a href="">d093907</a>)</li>
</ul>
<h2>v7.17.2</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.17.1...v7.17.2">7.17.2</a> (2022-10-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Consider source cache when setting search path for python scripts. This allows to import from Python modules next to scripts while deploying the workflow as a snakemake module, even from remote locations. (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1940">#1940</a>) (<a href="">27be1d4</a>)</li>
</ul>
<h2>v7.17.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.17.0...v7.17.1">7.17.1</a> (2022-10-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>change source cache entries to keep the original name and folder structure, such that imports from e.g. scripts also work with remote modules (if specified as additional input files with workflow.source_path) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1936">#1936</a>) (<a href="">c34f3f6</a>)</li>
</ul>
<h2>v7.17.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.16.2...v7.17.0">7.17.0</a> (2022-10-27)</h2>
<h3>Features</h3>
<ul>
<li>allow to define the cache mode per rule (this enables to exclude software envs from the caching hash value, which can be handy e.g. for download rules where the software version does not affect the result) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1933">#1933</a>) (<a href="">715e618</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.18.1...v7.18.2">7.18.2</a> (2022-11-10)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Change ratelimiter dependency to throttler (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1958">#1958</a>) (<a href="">50b8f16</a>)</li>
<li>fixed problem with leaked modifications when inheriting multiple times from the same rule (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1957">#1957</a>) (<a href="">2475cbc</a>)</li>
<li>forwarding --keep-incomplete to cluster executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1951">#1951</a>) (<a href="">2894c7d</a>)</li>
<li>show input files on job error (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1949">#1949</a>) (<a href="">ad21631</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.18.0...v7.18.1">7.18.1</a> (2022-11-03)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>regression ValueError introduced with 7.17.2 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1947">#1947</a>) (<a href="">53a4fca</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.17.2...v7.18.0">7.18.0</a> (2022-10-31)</h2>
<h3>Features</h3>
<ul>
<li>first try to match output files against input files while persisting wildcard values from the consuming job. This can dramatically reduce ambiuity problems. Thanks to <a href="https://github.com/descostesn"><code>@​descostesn</code></a>! (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1939">#1939</a>) (<a href="">d093907</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.17.1...v7.17.2">7.17.2</a> (2022-10-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>Consider source cache when setting search path for python scripts. This allows to import from Python modules next to scripts while deploying the workflow as a snakemake module, even from remote locations. (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1940">#1940</a>) (<a href="">27be1d4</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.17.0...v7.17.1">7.17.1</a> (2022-10-28)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>change source cache entries to keep the original name and folder structure, such that imports from e.g. scripts also work with remote modules (if specified as additional input files with workflow.source_path) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1936">#1936</a>) (<a href="">c34f3f6</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.16.2...v7.17.0">7.17.0</a> (2022-10-27)</h2>
<h3>Features</h3>
<ul>
<li>allow to define the cache mode per rule (this enables to exclude software envs from the caching hash value, which can be handy e.g. for download rules where the software version does not affect the result) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1933">#1933</a>) (<a href="">715e618</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>cached os.pathconf() call in _record_path() (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1920">#1920</a>) (<a href="">551badb</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a5c3523</code></a> chore(main): release 7.18.2 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1950">#1950</a>)</li>
<li><a href=""><code>50b8f16</code></a> fix: Change ratelimiter dependency to throttler (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1958">#1958</a>)</li>
<li><a href=""><code>2894c7d</code></a> fix: forwarding --keep-incomplete to cluster executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1951">#1951</a>)</li>
<li><a href=""><code>2475cbc</code></a> fix: fixed problem with leaked modifications when inheriting multiple times f...</li>
<li><a href=""><code>ad21631</code></a> fix: show input files on job error (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1949">#1949</a>)</li>
<li><a href=""><code>5858a34</code></a> Merge branch 'main' of github.com:snakemake/snakemake</li>
<li><a href=""><code>81bdb10</code></a> chore: use latest container image</li>
<li><a href=""><code>053eaa4</code></a> chore(main): release 7.18.1 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1948">#1948</a>)</li>
<li><a href=""><code>53a4fca</code></a> fix: regression ValueError introduced with 7.17.2 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1947">#1947</a>)</li>
<li><a href=""><code>ee07064</code></a> chore(deps): Bump marocchino/sticky-pull-request-comment from 2.2.1 to 2.3.0 ...</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.3.8...v7.18.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.3.8&new-version=7.18.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78ebc1e83aa7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.