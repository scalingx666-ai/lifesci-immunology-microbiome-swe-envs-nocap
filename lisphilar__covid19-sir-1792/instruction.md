# Issue

**Title:** build(deps): bump pca from 2.0.7 to 2.0.9

## Description

Bumps [pca](https://github.com/erdogant/pca) from 2.0.7 to 2.0.9.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/erdogant/pca/releases">pca's releases</a>.</em></p>
<blockquote>
<h2>2.0.8</h2>
<ul>
<li>Update for warning <code>get_cmap </code>when using matplotlib &gt;= 3.10 (Issue <a href="">#59</a>)</li>
<li>Fix for error in <code>biplot</code> that sometimes occurred (issue <a href="">#58</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1d15b2a</code></a> update req</li>
<li><a href=""><code>aab9053</code></a> remove version matplotlib</li>
<li><a href=""><code>3f3947c</code></a> pytest updates</li>
<li><a href=""><code>375a415</code></a> update versions</li>
<li><a href=""><code>9fc8810</code></a> update label assignment</li>
<li><a href=""><code>ea1d8d3</code></a> update cmap</li>
<li><a href=""><code>59c0cd1</code></a> update docs issue <a href="">#60</a></li>
<li><a href=""><code>24dd21c</code></a> update docs</li>
<li><a href=""><code>af1c943</code></a> update requirements</li>
<li><a href=""><code>8dd7b4c</code></a> update docstrings</li>
<li>See full diff in <a href="https://github.com/erdogant/pca/compare/2.0.7...2.0.9">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pca&package-manager=pip&previous-version=2.0.7&new-version=2.0.9)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

## Summary by Sourcery

Build:
- Bump pca dependency from 2.0.7 to 2.0.9.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d249d6482ca9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.