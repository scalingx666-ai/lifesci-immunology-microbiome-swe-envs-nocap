# Issue

**Title:** build(deps): bump pyarrow from 19.0.1 to 20.0.0

## Description

Bumps [pyarrow](https://github.com/apache/arrow) from 19.0.1 to 20.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 20.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/20.0.0.html">https://arrow.apache.org/release/20.0.0.html</a></p>
<h2>Apache Arrow 20.0.0 RC2</h2>
<p>Release Notes: Release Candidate: 20.0.0 RC2</p>
<h2>Apache Arrow 20.0.0 RC1</h2>
<p>Release Notes: Release Candidate: 20.0.0 RC1</p>
<h2>Apache Arrow 20.0.0 RC0</h2>
<p>Release Notes: Release Candidate: 20.0.0 RC0</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3ad0370</code></a> MINOR: [Release] Update versions for 20.0.0</li>
<li><a href=""><code>e4aed0d</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 20.0.0</li>
<li><a href=""><code>02f9dfb</code></a> MINOR: [Release] Update CHANGELOG.md for 20.0.0</li>
<li><a href=""><code>92c3e39</code></a> <a href="">GH-46077</a>: [CI][C++] Disable -Werror on macos-13 (<a href="">#46106</a>)</li>
<li><a href=""><code>2f82cd8</code></a> <a href="">GH-46123</a>: [C++] Undefined behavior in <code>compare_internal.cc</code> and `light_array_...</li>
<li><a href=""><code>af15118</code></a> <a href="">GH-46159</a>: [CI][C++] Stop using possibly missing boost/process/v2.hpp on boost...</li>
<li><a href=""><code>7a6eefe</code></a> <a href="">GH-46169</a>: [CI][R] Update R version to 4.5 due to 4.4 not being on APT reposit...</li>
<li><a href=""><code>5c1eb91</code></a> <a href="">GH-46167</a>: [R][CI] Update Artifacts for R 4.5 in task.yml (<a href="">#46168</a>)</li>
<li><a href=""><code>0f41ecc</code></a> <a href="">GH-45986</a>: [C++] Update bundled GoogleTest (<a href="">#45996</a>)</li>
<li><a href=""><code>1e2aa39</code></a> <a href="">GH-46075</a>: [Release][CI] Fix binary verification (<a href="">#46076</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/apache-arrow-19.0.1...apache-arrow-20.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pyarrow&package-manager=pip&previous-version=19.0.1&new-version=20.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump pyarrow version constraint to allow version 20.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b72c1481e01c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.