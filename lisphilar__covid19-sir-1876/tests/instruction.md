# Issue

**Title:** build(deps): bump pyarrow from 21.0.0 to 22.0.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Bumps [pyarrow](https://github.com/apache/arrow) from 21.0.0 to 22.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 22.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/22.0.0.html">https://arrow.apache.org/release/22.0.0.html</a></p>
<h2>Apache Arrow 22.0.0 RC1</h2>
<p>Release Notes: Release Candidate: 22.0.0 RC1</p>
<h2>Apache Arrow 22.0.0 RC0</h2>
<p>Release Notes: Release Candidate: 22.0.0 RC0</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5aeb5f2</code></a> MINOR: [Release] Update versions for 22.0.0</li>
<li><a href=""><code>81563ad</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 22.0.0</li>
<li><a href=""><code>c505536</code></a> MINOR: [Release] Update CHANGELOG.md for 22.0.0</li>
<li><a href=""><code>e04fafb</code></a> <a href="">GH-47838</a>: [C++][Parquet] Set Variant specification version to 1 to align with...</li>
<li><a href=""><code>07e4d5a</code></a> <a href="">GH-47819</a>: [CI][Packaging][Release] Avoid triggering Linux packages on release...</li>
<li><a href=""><code>e2fa94c</code></a> <a href="">GH-47809</a>: [CI][Release] Fix Windows verification job trying to install patch ...</li>
<li><a href=""><code>2140934</code></a> <a href="">GH-47738</a>: [R] Update NEWS.md for 22.0.0 (<a href="">#47739</a>)</li>
<li><a href=""><code>08f5304</code></a> <a href="">GH-47803</a>: [C++][Parquet] Fix read out of bounds on invalid RLE data (<a href="">#47804</a>)</li>
<li><a href=""><code>d5b8e2b</code></a> <a href="">GH-47438</a>: [Python][Packaging] Set up wheel building for Python 3.14 (<a href="">#47616</a>)</li>
<li><a href=""><code>618f609</code></a> <a href="">GH-47795</a>: [Archery] Add support for custom Docker registry (<a href="">#47796</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/apache-arrow-21.0.0...apache-arrow-22.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pyarrow&package-manager=pip&previous-version=21.0.0&new-version=22.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d184a1d1791f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.