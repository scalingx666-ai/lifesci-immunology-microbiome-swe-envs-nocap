# Issue

**Title:** build(deps): bump pyarrow from 17.0.0 to 18.0.0

## Description

Bumps [pyarrow](https://github.com/apache/arrow) from 17.0.0 to 18.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 18.0.0</h2>
<p>TODO</p>
<h2>Apache Arrow 18.0.0 RC0</h2>
<p>Release Notes: Release Candidate: 18.0.0 RC0</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9105a41</code></a> MINOR: [Release] Update versions for 18.0.0</li>
<li><a href=""><code>e47bf46</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 18.0.0</li>
<li><a href=""><code>8567163</code></a> MINOR: [Release] Update CHANGELOG.md for 18.0.0</li>
<li><a href=""><code>5d7987b</code></a> <a href="">GH-44422</a>: [Packaging][Release][Linux] Upload artifacts before test (<a href="">#44425</a>)</li>
<li><a href=""><code>70a2245</code></a> <a href="">GH-44415</a>: [Release][Ruby] Remove pins from glib section of release verificati...</li>
<li><a href=""><code>155a42e</code></a> <a href="">GH-44342</a>: [C++] Disable jemalloc by default on ARM (<a href="">#44380</a>)</li>
<li><a href=""><code>0e184c3</code></a> <a href="">GH-44386</a>: [Integration][Release] Pin Python 3.12 for Integration verification...</li>
<li><a href=""><code>9812ab7</code></a> <a href="">GH-44381</a>: [Ruby][Release] Pin not only glib but also python on verification j...</li>
<li><a href=""><code>71bd117</code></a> <a href="">GH-43519</a>: [Python][CI] Add Python 3.13 conda test build (<a href="">#44192</a>)</li>
<li><a href=""><code>a39090d</code></a> <a href="">GH-44373</a>: [Packaging][Java] Fix brew link to Python 3.13 on macOS (<a href="">#44374</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/go/v17.0.0...apache-arrow-18.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pyarrow&package-manager=pip&previous-version=17.0.0&new-version=18.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c71ef36990c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.