# Issue

**Title:** build(deps): update pyarrow requirement from <25,>=15 to >=15,<26

## Description

Updates the requirements on [pyarrow](https://github.com/apache/arrow) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 25.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/25.0.0.html">https://arrow.apache.org/release/25.0.0.html</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>59bea6e</code></a> MINOR: [Release] Update versions for 25.0.0</li>
<li><a href=""><code>381fab6</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 25.0.0</li>
<li><a href=""><code>7f72d5b</code></a> MINOR: [Release] Update CHANGELOG.md for 25.0.0</li>
<li><a href=""><code>fe2f85c</code></a> <a href="">GH-50336</a>: [Release][Archery] Fix archery GitHub integration for release scrip...</li>
<li><a href=""><code>c658548</code></a> <a href="">GH-50293</a>: [CI] Run check-labels for all triggers to avoid cancelling further ...</li>
<li><a href=""><code>f83c8ca</code></a> <a href="">GH-50330</a>: [C++][R][Parquet] Add missing typename in RleBitPackedDecoderGetRun...</li>
<li><a href=""><code>35e0f63</code></a> <a href="">GH-50318</a>: [R][CI] Install missing libpng-dev for test-r-linux-as-cran (<a href="">#50328</a>)</li>
<li><a href=""><code>61ca7a9</code></a> <a href="">GH-50295</a>: [C++][R] #include &lt;ranges&gt; in vector_select_k.cc breaks macOS CRAN ...</li>
<li><a href=""><code>1b6edb8</code></a> <a href="">GH-50291</a>: [Python][Packaging] Stop using nightly build dependencies for build...</li>
<li><a href=""><code>e183ea9</code></a> MINOR: [Docs] Add Timestamp With Offset to canonical extension types status (...</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/go/v15.0.0...apache-arrow-25.0.0">compare view</a></li>
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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `674db49f4bbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.