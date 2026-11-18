# Issue

**Title:** build(deps): update rust-htslib requirement from 0.38.* to 0.39.*

## Description

Updates the requirements on [rust-htslib](https://github.com/rust-bio/rust-htslib) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-bio/rust-htslib/releases">rust-htslib's releases</a>.</em></p>
<blockquote>
<h2>rust-htslib rust-htslib-v0.39.5</h2>
<h3>Bug Fixes</h3>
<ul>
<li>set path in release-please config (<a href="">d8f7c6e</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-bio/rust-htslib/blob/master/CHANGELOG.md">rust-htslib's changelog</a>.</em></p>
<blockquote>
<h3><a href="https://www.github.com/rust-bio/rust-htslib/compare/rust-htslib-v0.39.4...rust-htslib-v0.39.5">0.39.5</a> (2022-05-09)</h3>
<h3>Bug Fixes</h3>
<ul>
<li>set path in release-please config (<a href="">d8f7c6e</a>)</li>
</ul>
<h3><a href="https://www.github.com/rust-bio/rust-htslib/compare/rust-htslib-v0.39.3...rust-htslib-v0.39.4">0.39.4</a> (2022-05-09)</h3>
<h3>Bug Fixes</h3>
<ul>
<li>perform checkout before running release please (<a href="">cbc6a0a</a>)</li>
</ul>
<h3><a href="https://www.github.com/rust-bio/rust-htslib/compare/rust-htslib-v0.39.2...rust-htslib-v0.39.3">0.39.3</a> (2021-11-20)</h3>
<h3>Bug Fixes</h3>
<ul>
<li>change the type to c_char so it can be compiled for aarch64 (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/337">#337</a>) (<a href="">a21aff2</a>)</li>
</ul>
<h3><a href="https://www.github.com/rust-bio/rust-htslib/compare/rust-htslib-v0.39.1...rust-htslib-v0.39.2">0.39.2</a> (2021-08-23)</h3>
<h3>Bug Fixes</h3>
<ul>
<li>Configuration when cross-compiling. Even when cross-compiling, build.rs runs on the build host. Hence within build.rs <code>#[cfg(target_os)]</code> always reflects the host, not the target. Use $CARGO_CFG_TARGET_OS instead to query target properties. (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/329">#329</a>) (<a href="">d5198e6</a>)</li>
</ul>
<h3><a href="https://www.github.com/rust-bio/rust-htslib/compare/rust-htslib-v0.39.0...rust-htslib-v0.39.1">0.39.1</a> (2021-07-06)</h3>
<h3>Bug Fixes</h3>
<ul>
<li>bump hts-sys version to 2.0.1 (<a href="">336c8b8</a>)</li>
</ul>
<h2><a href="https://www.github.com/rust-bio/rust-htslib/compare/rust-htslib-vrust-htslib-0.38.3...rust-htslib-v0.39.0">0.39.0</a> (2021-07-06)</h2>
<h3>⚠ BREAKING CHANGES</h3>
<ul>
<li>dummy major version bump to move away from previous versions that were following htslib versions.</li>
<li>bump to new major version (for technical reasons).</li>
<li>dummy breaking change to increase hts-sys major version.</li>
</ul>
<h3>Bug Fixes</h3>
<ul>
<li>bump to new major version (for technical reasons). (<a href="">9c6db30</a>)</li>
<li>dummy breaking change to increase hts-sys major version. (<a href="">93415cb</a>)</li>
<li>dummy changes (<a href="">3af5ede</a>)</li>
<li>dummy major version bump to move away from previous versions that were following htslib versions. (<a href="">aaa70a8</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bdebe65</code></a> chore: release rust-htslib 0.39.5 (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/356">#356</a>)</li>
<li><a href=""><code>d8f7c6e</code></a> fix: set path in release-please config</li>
<li><a href=""><code>5fb5779</code></a> chore: release rust-htslib 0.39.4 (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/355">#355</a>)</li>
<li><a href=""><code>cbc6a0a</code></a> fix: perform checkout before running release please</li>
<li><a href=""><code>5453450</code></a> chore: release rust-htslib 0.39.3 (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/338">#338</a>)</li>
<li><a href=""><code>e3c8e81</code></a> Update libdeflater dep (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/341">#341</a>)</li>
<li><a href=""><code>a21aff2</code></a> fix: change the type to c_char so it can be compiled for aarch64 (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/337">#337</a>)</li>
<li><a href=""><code>c7f68a7</code></a> hotfix: override matrix-derived toolchain installation for now</li>
<li><a href=""><code>2249e09</code></a> matrix.os is empty for this workflow</li>
<li><a href=""><code>eeb08be</code></a> chore: Exclude test files from crate package. (<a href="https://github-redirect.dependabot.com/rust-bio/rust-htslib/issues/336">#336</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/rust-bio/rust-htslib/compare/rust-htslib-0.38.3...rust-htslib-v0.39.5">compare view</a></li>
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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ff59e476de0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.