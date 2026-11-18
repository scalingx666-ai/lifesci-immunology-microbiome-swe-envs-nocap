# Issue

**Title:** build(deps): update pyarrow requirement from <24,>=15 to >=15,<25

## Description

Updates the requirements on [pyarrow](https://github.com/apache/arrow) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/apache/arrow/releases">pyarrow's releases</a>.</em></p>
<blockquote>
<h2>Apache Arrow 24.0.0</h2>
<p>Release Notes URL: <a href="https://arrow.apache.org/release/24.0.0.html">https://arrow.apache.org/release/24.0.0.html</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>31b4b6c</code></a> MINOR: [Release] Update versions for 24.0.0</li>
<li><a href=""><code>06dbc17</code></a> MINOR: [Release] Update .deb/.rpm changelogs for 24.0.0</li>
<li><a href=""><code>a021d80</code></a> MINOR: [Release] Update CHANGELOG.md for 24.0.0</li>
<li><a href=""><code>2d6b12c</code></a> <a href="">GH-49716</a>: [C++] FixedShapeTensorType::Deserialize should strictly validate se...</li>
<li><a href=""><code>a74cb6a</code></a> <a href="">GH-49697</a>: [C++][CI] Check IPC file body bounds are in sync with decoder outco...</li>
<li><a href=""><code>871a0c6</code></a> <a href="">GH-49676</a>: [Python][Packaging] Fix gRPC docker image layer being too big for h...</li>
<li><a href=""><code>f9203b3</code></a> <a href="">GH-49586</a>: [C++][CI] StructToStructSubset test failure with libc++ 22.1.1 (<a href="">#49</a>...</li>
<li><a href=""><code>fe298b4</code></a> <a href="">GH-49628</a>: [Python][Interchange protocol] Suppress warnings for pandas 4.0.0 a...</li>
<li><a href=""><code>1f94910</code></a> <a href="">GH-49252</a>: [GLib] Deprecate Feather features (<a href="">#49673</a>)</li>
<li><a href=""><code>5ba5c3c</code></a> <a href="">GH-49671</a>: [CI][Docs] Don't run jobs for push by Dependabot (<a href="">#49672</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/apache/arrow/compare/go/v15.0.0...apache-arrow-24.0.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f588d42784d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.