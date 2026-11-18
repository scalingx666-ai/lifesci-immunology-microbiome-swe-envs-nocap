# Issue

**Title:** build(deps): update pyarrow requirement from <23,>=15 to >=15,<24

## Description

Updates the requirements on [pyarrow](https://github.com/apache/arrow) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 23.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/23.0.0.html">https://arrow.apache.org/release/23.0.0.html</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>eafe3a9</code></a> MINOR: [Release] Update versions for 23.0.0</li>
<li><a href=""><code>45781e8</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 23.0.0</li>
<li><a href=""><code>365e5ac</code></a> MINOR: [Release] Update CHANGELOG.md for 23.0.0</li>
<li><a href=""><code>e33512d</code></a> <a href="">GH-48841</a>: [Release][Package] Add GH_TOKEN to rake build step on Linux Packagi...</li>
<li><a href=""><code>86d28e9</code></a> <a href="">GH-48838</a>: [Release] Use gh cli to download sources for Linux packages and pub...</li>
<li><a href=""><code>b6362d0</code></a> <a href="">GH-48582</a>: [CI][GPU][C++][Python] Add new CUDA jobs using the new self-hosted ...</li>
<li><a href=""><code>8fb7a53</code></a> <a href="">GH-48827</a>: [CI][Python] Add required xz dependency to emscripten dockerfile (#...</li>
<li><a href=""><code>342c5d5</code></a> <a href="">GH-48809</a>: [CI] Fix homebrew-cpp with Mac by using formula-based dependency re...</li>
<li><a href=""><code>8955bbf</code></a> <a href="">GH-48631</a>: [R] Non-API calls: 'ATTRIB', 'SET_ATTRIB' (<a href="">#48634</a>)</li>
<li><a href=""><code>b90a2b8</code></a> <a href="">GH-48314</a>: [Python] Compat with pandas 3.0 changed default datetime unit (<a href="">#48319</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/go/v15.0.0...apache-arrow-23.0.0">compare view</a></li>
</ul>
</details>
<br />

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0638676f15c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.