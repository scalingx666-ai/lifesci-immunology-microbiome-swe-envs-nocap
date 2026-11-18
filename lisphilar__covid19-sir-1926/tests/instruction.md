# Issue

**Title:** build(deps): bump pyarrow from 22.0.0 to 23.0.1

## Description

Bumps [pyarrow](https://github.com/apache/arrow) from 22.0.0 to 23.0.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 23.0.1</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/23.0.1.html">https://arrow.apache.org/release/23.0.1.html</a></p>
<h2>Apache Arrow 23.0.1 RC0</h2>
<p>Release Notes: Release Candidate: 23.0.1 RC0</p>
<h2>Apache Arrow 23.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/23.0.0.html">https://arrow.apache.org/release/23.0.0.html</a></p>
<h2>Apache Arrow 23.0.0 RC2</h2>
<p>Release Notes: Release Candidate: 23.0.0 RC2</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>82a374e</code></a> MINOR: [Release] Update versions for 23.0.1</li>
<li><a href=""><code>c1ae37c</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 23.0.1</li>
<li><a href=""><code>8f6e557</code></a> MINOR: [Release] Update CHANGELOG.md for 23.0.1</li>
<li><a href=""><code>4e16a1a</code></a> <a href="">GH-49159</a>: [C++][Gandiva] Detect overflow in repeat() (<a href="">#49160</a>)</li>
<li><a href=""><code>985621d</code></a> <a href="">GH-48817</a> [R][C++] Bump C++20 in R build infrastructure (<a href="">#48819</a>)</li>
<li><a href=""><code>1bea06a</code></a> <a href="">GH-49024</a>: [CI] Update Debian version in <code>.env</code> (<a href="">#49032</a>)</li>
<li><a href=""><code>147bcd6</code></a> <a href="">GH-49156</a>: [Python] Require GIL for string comparison (<a href="">#49161</a>)</li>
<li><a href=""><code>e4f922b</code></a> <a href="">GH-49138</a>: [Packaging][Python] Remove nightly cython install from manylinux wh...</li>
<li><a href=""><code>f9376e4</code></a> <a href="">GH-49003</a>: [C++] Don't consider <code>out_of_range</code> an error in float parsing (<a href="">#49095</a>)</li>
<li><a href=""><code>ab2c0ad</code></a> <a href="">GH-49044</a>: [CI][Python] Fix test_download_tzdata_on_windows by adding required...</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/apache-arrow-22.0.0...apache-arrow-23.0.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pyarrow&package-manager=uv&previous-version=22.0.0&new-version=23.0.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lisphilar/covid19-sir/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `265c783bb85b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.