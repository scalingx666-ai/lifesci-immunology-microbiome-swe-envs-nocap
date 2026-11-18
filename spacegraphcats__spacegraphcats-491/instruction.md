# Issue

**Title:** Bump snakemake from 7.21.0 to 7.24.0

## Description

Bumps [snakemake](https://github.com/snakemake/snakemake) from 7.21.0 to 7.24.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/releases">snakemake's releases</a>.</em></p>
<blockquote>
<h2>v7.24.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.23.1...v7.24.0">7.24.0</a> (2023-03-01)</h2>
<h3>Features</h3>
<ul>
<li>limit the number of input/output files in job properties (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2149">#2149</a>) (<a href="">d93f091</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2130">#2130</a> by patching the protect() method so the path of files in subdirectories is properly resolved during write-protection (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2131">#2131</a>) (<a href="">1a754fd</a>)</li>
<li><code>sre_constants</code> import because of deprecation (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2139">#2139</a>) (<a href="">3b326db</a>)</li>
<li>ensure user and group rw permissions for metadata files and source cache (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2132">#2132</a>) (<a href="">cc51faa</a>)</li>
<li>is_run error with local, group jobs (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2133">#2133</a>) (<a href="">31bfcd5</a>)</li>
<li>require toposort &gt;= 1.10 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2145">#2145</a>) (<a href="">3cb54b8</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Update modularization.rst (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2137">#2137</a>) (<a href="">16954c7</a>)</li>
</ul>
<h2>v7.23.1</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.23.0...v7.23.1">7.23.1</a> (2023-02-18)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>batch collect jobs for scancel (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2114">#2114</a>) (<a href="">0b1fe31</a>)</li>
</ul>
<h2>v7.23.0</h2>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.22.0...v7.23.0">7.23.0</a> (2023-02-18)</h2>
<h3>Features</h3>
<ul>
<li>changed report layout to display menu always left of the results. For fullscreen, one can still hide the menu, which leads to automatic growth of the results (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2116">#2116</a>) (<a href="">d771b1b</a>)</li>
<li>Publish docker images for amd64 &amp; arm64 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2105">#2105</a>) (<a href="">4c898f5</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>use text/markdown for long_description_content_type (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2112">#2112</a>) (<a href="">0241075</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>Improve execution speed of cleanup_workdir (in dag)  (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2103">#2103</a>) (<a href="">1fbc5f5</a>)</li>
</ul>
<h2>v7.22.0</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/snakemake/snakemake/blob/main/CHANGELOG.md">snakemake's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.23.1...v7.24.0">7.24.0</a> (2023-03-01)</h2>
<h3>Features</h3>
<ul>
<li>limit the number of input/output files in job properties (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2149">#2149</a>) (<a href="">d93f091</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li><a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2130">#2130</a> by patching the protect() method so the path of files in subdirectories is properly resolved during write-protection (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2131">#2131</a>) (<a href="">1a754fd</a>)</li>
<li><code>sre_constants</code> import because of deprecation (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2139">#2139</a>) (<a href="">3b326db</a>)</li>
<li>ensure user and group rw permissions for metadata files and source cache (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2132">#2132</a>) (<a href="">cc51faa</a>)</li>
<li>is_run error with local, group jobs (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2133">#2133</a>) (<a href="">31bfcd5</a>)</li>
<li>require toposort &gt;= 1.10 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2145">#2145</a>) (<a href="">3cb54b8</a>)</li>
</ul>
<h3>Documentation</h3>
<ul>
<li>Update modularization.rst (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2137">#2137</a>) (<a href="">16954c7</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.23.0...v7.23.1">7.23.1</a> (2023-02-18)</h2>
<h3>Bug Fixes</h3>
<ul>
<li>batch collect jobs for scancel (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2114">#2114</a>) (<a href="">0b1fe31</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.22.0...v7.23.0">7.23.0</a> (2023-02-18)</h2>
<h3>Features</h3>
<ul>
<li>changed report layout to display menu always left of the results. For fullscreen, one can still hide the menu, which leads to automatic growth of the results (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2116">#2116</a>) (<a href="">d771b1b</a>)</li>
<li>Publish docker images for amd64 &amp; arm64 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2105">#2105</a>) (<a href="">4c898f5</a>)</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>use text/markdown for long_description_content_type (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2112">#2112</a>) (<a href="">0241075</a>)</li>
</ul>
<h3>Performance Improvements</h3>
<ul>
<li>Improve execution speed of cleanup_workdir (in dag)  (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2103">#2103</a>) (<a href="">1fbc5f5</a>)</li>
</ul>
<h2><a href="https://github.com/snakemake/snakemake/compare/v7.21.0...v7.22.0">7.22.0</a> (2023-02-12)</h2>
<h3>Features</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c892446</code></a> chore(main): release 7.24.0 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2144">#2144</a>)</li>
<li><a href=""><code>f07d779</code></a> refactor: add missing linebreak in error handling (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2082">#2082</a>)</li>
<li><a href=""><code>3b326db</code></a> fix: <code>sre_constants</code> import because of deprecation (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2139">#2139</a>)</li>
<li><a href=""><code>d93f091</code></a> feat: limit the number of input/output files in job properties (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2149">#2149</a>)</li>
<li><a href=""><code>cc51faa</code></a> fix: ensure user and group rw permissions for metadata files and source cache...</li>
<li><a href=""><code>3cb54b8</code></a> fix: require toposort &gt;= 1.10 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2145">#2145</a>)</li>
<li><a href=""><code>1a754fd</code></a> fix: <a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2130">#2130</a> by patching the protect() method so the path of files in subdirect...</li>
<li><a href=""><code>16954c7</code></a> docs: Update modularization.rst (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2137">#2137</a>)</li>
<li><a href=""><code>31bfcd5</code></a> fix: is_run error with local, group jobs (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2133">#2133</a>)</li>
<li><a href=""><code>a110ae0</code></a> chore(main): release 7.23.1 (<a href="https://github-redirect.dependabot.com/snakemake/snakemake/issues/2119">#2119</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/snakemake/snakemake/compare/v7.21.0...v7.24.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=snakemake&package-manager=pip&previous-version=7.21.0&new-version=7.24.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0d9dbc12f8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.