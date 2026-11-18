# Issue

**Title:** build(deps): bump pyarrow from 18.1.0 to 19.0.0

## Description

Bumps [pyarrow](https://github.com/apache/arrow) from 18.1.0 to 19.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 19.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/19.0.0.html">https://arrow.apache.org/release/19.0.0.html</a></p>
<h2>Apache Arrow 19.0.0 RC0</h2>
<p>Release Notes: Release Candidate: 19.0.0 RC0</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a999eac</code></a> MINOR: [Release] Update versions for 19.0.0</li>
<li><a href=""><code>f6b7bc8</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 19.0.0</li>
<li><a href=""><code>848fde3</code></a> MINOR: [Release] Update CHANGELOG.md for 19.0.0</li>
<li><a href=""><code>8677e33</code></a> <a href="">GH-45175</a>: [Python] Honor the strings_to_categorical keyword in to_pandas for ...</li>
<li><a href=""><code>f41f590</code></a> <a href="">GH-45166</a>: [CI][C++] Upgrade Alpine Linux to 3.18 from 3.16 (<a href="">#45168</a>)</li>
<li><a href=""><code>8cff21f</code></a> <a href="">GH-45178</a>: [CI] Remove clcache related codes (<a href="">#45182</a>)</li>
<li><a href=""><code>777797e</code></a> <a href="">GH-45183</a>: [C++][Release] Add llvm-dev back to setup-ubuntu.sh (<a href="">#45184</a>)</li>
<li><a href=""><code>14dc66d</code></a> MINOR: [C#] Bump coverlet.collector from 6.0.2 to 6.0.3 in /csharp (<a href="">#45179</a>)</li>
<li><a href=""><code>a931aff</code></a> <a href="">GH-45073</a>: [C++][Parquet] Fix generation of repetition levels for encryption t...</li>
<li><a href=""><code>ada8750</code></a> <a href="">GH-44563</a>: [C++] <code>FunctionOptions::{Serialize,Deserialize}()</code> return an error ...</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/apache-arrow-18.1.0...apache-arrow-19.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pyarrow&package-manager=pip&previous-version=18.1.0&new-version=19.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f77e280322a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.