# Issue

**Title:** Bump snakemake from 7.19.1 to 7.20.0

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.19.1 to 7.20.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.20.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.19.1...v7.20.0">7.20.0</a> (2023-01-18)</h2>
<h3>Features</h3>
<ul>
<li>add tes token (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1966">#1966</a>) (<a href="">59a8fa0</a>)</li>
<li>Add token auth to GitLab/GitHub hosting providers (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1761">#1761</a>) (<a href="">e03a3b4</a>), closes <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1301">#1301</a></li>
<li>allow for human friendly resource definitions (e.g. mem=&quot;5GB&quot;, runtime=&quot;1d&quot;) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1861">#1861</a>) (<a href="">24610ac</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>:bug: - fix hyperlink (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2046">#2046</a>) (<a href="">9519d31</a>)</li>
<li>Catch missing error stream in Slurm executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2063">#2063</a>) (<a href="">c21fc7e</a>)</li>
<li>correctly parse empty values in config cli (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2032">#2032</a>) (<a href="">1b0689d</a>)</li>
<li>Correctly parse UserDicts in executors (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2016">#2016</a>) (<a href="">e3926fa</a>)</li>
<li>Fix handling of --jobs in no-exec state (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2029">#2029</a>) (<a href="">e8e8222</a>)</li>
<li>make <code>--show-failed-logs</code> handle empty log files (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2039">#2039</a>) (<a href="">683c6f2</a>), closes <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2023">#2023</a></li>
<li>make python version check more robust (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2058">#2058</a>) (<a href="">e685621</a>)</li>
<li>parsing error when last line is comment (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2054">#2054</a>) (<a href="">a928dd4</a>)</li>
<li>prevent overriding of retries when set to 0 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2053">#2053</a>) (<a href="">a328f3e</a>)</li>
<li>propagate attempt count from group to subjobs (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2052">#2052</a>) (<a href="">da3f1c0</a>)</li>
<li>remove overflow from rulegraph div in report (<a href="">9a0aaa7</a>)</li>
<li>skip type checks of missing dir in touch mode (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2051">#2051</a>) (<a href="">ae00c25</a>)</li>
<li>slurm default_resources quoting (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2043">#2043</a>) (<a href="">47d3fc3</a>)</li>
<li>Update list of python versions in classifiers (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2020">#2020</a>) (<a href="">7a98100</a>)</li>
<li>use short argument name for <code>--chdir</code> for compatibility with Slurm &lt;=v17 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2040">#2040</a>) (<a href="">a9ed3ec</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix typo in SLURM help text (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2049">#2049</a>) (<a href="">79b7025</a>)</li>
<li>mention XDG_CACHE_HOME (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2057">#2057</a>) (<a href="">ec2ef45</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.19.1...v7.20.0">7.20.0</a> (2023-01-18)</h2>
<h3>Features</h3>
<ul>
<li>add tes token (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1966">#1966</a>) (<a href="">59a8fa0</a>)</li>
<li>Add token auth to GitLab/GitHub hosting providers (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1761">#1761</a>) (<a href="">e03a3b4</a>), closes <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1301">#1301</a></li>
<li>allow for human friendly resource definitions (e.g. mem=&quot;5GB&quot;, runtime=&quot;1d&quot;) (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/1861">#1861</a>) (<a href="">24610ac</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>:bug: - fix hyperlink (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2046">#2046</a>) (<a href="">9519d31</a>)</li>
<li>Catch missing error stream in Slurm executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2063">#2063</a>) (<a href="">c21fc7e</a>)</li>
<li>correctly parse empty values in config cli (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2032">#2032</a>) (<a href="">1b0689d</a>)</li>
<li>Correctly parse UserDicts in executors (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2016">#2016</a>) (<a href="">e3926fa</a>)</li>
<li>Fix handling of --jobs in no-exec state (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2029">#2029</a>) (<a href="">e8e8222</a>)</li>
<li>make <code>--show-failed-logs</code> handle empty log files (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2039">#2039</a>) (<a href="">683c6f2</a>), closes <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2023">#2023</a></li>
<li>make python version check more robust (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2058">#2058</a>) (<a href="">e685621</a>)</li>
<li>parsing error when last line is comment (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2054">#2054</a>) (<a href="">a928dd4</a>)</li>
<li>prevent overriding of retries when set to 0 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2053">#2053</a>) (<a href="">a328f3e</a>)</li>
<li>propagate attempt count from group to subjobs (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2052">#2052</a>) (<a href="">da3f1c0</a>)</li>
<li>remove overflow from rulegraph div in report (<a href="">9a0aaa7</a>)</li>
<li>skip type checks of missing dir in touch mode (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2051">#2051</a>) (<a href="">ae00c25</a>)</li>
<li>slurm default_resources quoting (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2043">#2043</a>) (<a href="">47d3fc3</a>)</li>
<li>Update list of python versions in classifiers (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2020">#2020</a>) (<a href="">7a98100</a>)</li>
<li>use short argument name for <code>--chdir</code> for compatibility with Slurm &lt;=v17 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2040">#2040</a>) (<a href="">a9ed3ec</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Fix typo in SLURM help text (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2049">#2049</a>) (<a href="">79b7025</a>)</li>
<li>mention XDG_CACHE_HOME (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2057">#2057</a>) (<a href="">ec2ef45</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1c9ea65</code></a> chore(main): release 7.20.0 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2018">#2018</a>)</li>
<li><a href=""><code>d326758</code></a> refactor: move static metadata (again) to setup.cfg (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2067">#2067</a>)</li>
<li><a href=""><code>c21fc7e</code></a> fix: Catch missing error stream in Slurm executor (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2063">#2063</a>)</li>
<li><a href=""><code>24610ac</code></a> feat: allow for human friendly resource definitions (e.g. mem=&quot;5GB&quot;, runtime=...</li>
<li><a href=""><code>2b07093</code></a> refactor: update versioneer from 0.18-&gt;0.28, clean-up setup.py/.cfg (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2065">#2065</a>)</li>
<li><a href=""><code>14042ce</code></a> refactor: move static metadata from setup.py to pyproject.toml (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2026">#2026</a>)</li>
<li><a href=""><code>ec2ef45</code></a> docs: mention XDG_CACHE_HOME (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2057">#2057</a>)</li>
<li><a href=""><code>a9ed3ec</code></a> fix: use short argument name for <code>--chdir</code> for compatibility with Slurm &lt;=v17...</li>
<li><a href=""><code>e685621</code></a> fix: make python version check more robust (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2058">#2058</a>)</li>
<li><a href=""><code>9a0aaa7</code></a> fix: remove overflow from rulegraph div in report</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.19.1...v7.20.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.19.1&new-version=7.20.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e12bd97d3da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.