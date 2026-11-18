# Issue

**Title:** Build(deps-rs): Bump the dependencies group across 1 directory with 5 updates

## Description

Bumps the dependencies group with 5 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [camino](https://github.com/camino-rs/camino) | `1.2.0` | `1.2.1` |
| [serde](https://github.com/serde-rs/serde) | `1.0.225` | `1.0.228` |
| [thiserror](https://github.com/dtolnay/thiserror) | `2.0.16` | `2.0.17` |
| [proptest](https://github.com/proptest-rs/proptest) | `1.7.0` | `1.8.0` |
| [tempfile](https://github.com/Stebalien/tempfile) | `3.22.0` | `3.23.0` |

Updates `camino` from 1.2.0 to 1.2.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/releases">camino's releases</a>.</em></p>
<blockquote>
<h2>camino 1.2.1</h2>
<h3>Fixed</h3>
<p>Replaced obsolete <code>doc_auto_cfg</code> with <code>doc_cfg</code>, to fix Rust nightly builds with the <code>doc_cfg</code> flag enabled.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/blob/main/CHANGELOG.md">camino's changelog</a>.</em></p>
<blockquote>
<h2>[1.2.1] - 2025-09-29</h2>
<h3>Fixed</h3>
<p>Replaced obsolete <code>doc_auto_cfg</code> with <code>doc_cfg</code>, to fix Rust nightly builds with the <code>doc_cfg</code> flag enabled.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>28e15db</code></a> [camino] version 1.2.1</li>
<li><a href=""><code>f32d994</code></a> prepare release</li>
<li><a href=""><code>ea187e4</code></a> remove doc_auto_cfg (<a href="">#114</a>)</li>
<li><a href=""><code>b0c8086</code></a> remove references to dead features from README</li>
<li>See full diff in <a href="https://github.com/camino-rs/camino/compare/camino-1.2.0...camino-1.2.1">compare view</a></li>
</ul>
</details>
<br />

Updates `serde` from 1.0.225 to 1.0.228
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/serde/releases">serde's releases</a>.</em></p>
<blockquote>
<h2>v1.0.228</h2>
<ul>
<li>Allow building documentation with <code>RUSTDOCFLAGS='--cfg=docsrs'</code> set for the whole dependency graph (<a href="">#2995</a>)</li>
</ul>
<h2>v1.0.227</h2>
<ul>
<li>Documentation improvements (<a href="">#2991</a>)</li>
</ul>
<h2>v1.0.226</h2>
<ul>
<li>Deduplicate variant matching logic inside generated Deserialize impl for adjacently tagged enums (<a href="">#2935</a>, thanks <a href="https://github.com/Mingun"><code>@​Mingun</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a866b33</code></a> Release 1.0.228</li>
<li><a href=""><code>5adc9e8</code></a> Merge pull request <a href="">#2995</a> from dtolnay/rustdocflags</li>
<li><a href=""><code>ab58178</code></a> Workaround for RUSTDOCFLAGS='--cfg=docsrs'</li>
<li><a href=""><code>415d9fc</code></a> Release 1.0.227</li>
<li><a href=""><code>7c58427</code></a> Merge pull request <a href="">#2991</a> from dtolnay/inlinecoredoc</li>
<li><a href=""><code>9d3410e</code></a> Merge pull request <a href="">#2992</a> from dtolnay/inplaceseed</li>
<li><a href=""><code>2fb6748</code></a> Remove InPlaceSeed public re-export</li>
<li><a href=""><code>f8137c7</code></a> Inline serde_core into serde in docsrs mode</li>
<li><a href=""><code>b7dbf7e</code></a> Merge pull request <a href="">#2990</a> from dtolnay/integer128</li>
<li><a href=""><code>7c83691</code></a> No longer macro_use integer128 module</li>
<li>Additional commits viewable in <a href="https://github.com/serde-rs/serde/compare/v1.0.225...v1.0.228">compare view</a></li>
</ul>
</details>
<br />

Updates `thiserror` from 2.0.16 to 2.0.17
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/dtolnay/thiserror/releases">thiserror's releases</a>.</em></p>
<blockquote>
<h2>2.0.17</h2>
<ul>
<li>Use differently named __private module per patch release (<a href="">#434</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>72ae716</code></a> Release 2.0.17</li>
<li><a href=""><code>599fdce</code></a> Merge pull request <a href="">#434</a> from dtolnay/private</li>
<li><a href=""><code>9ec05f6</code></a> Use differently named __private module per patch release</li>
<li><a href=""><code>d2c492b</code></a> Raise minimum tested compiler to rust 1.76</li>
<li><a href=""><code>fc3ab95</code></a> Opt in to generate-macro-expansion when building on docs.rs</li>
<li><a href=""><code>819fe29</code></a> Update ui test suite to nightly-2025-09-12</li>
<li><a href=""><code>259f48c</code></a> Enforce trybuild &gt;= 1.0.108</li>
<li><a href=""><code>470e6a6</code></a> Update ui test suite to nightly-2025-08-24</li>
<li><a href=""><code>544e191</code></a> Update actions/checkout@v4 -&gt; v5</li>
<li><a href=""><code>cbc1eba</code></a> Delete duplicate cap-lints flag from build script</li>
<li>See full diff in <a href="https://github.com/dtolnay/thiserror/compare/2.0.16...2.0.17">compare view</a></li>
</ul>
</details>
<br />

Updates `proptest` from 1.7.0 to 1.8.0
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>2885bc2</code></a> new releases for proptest, proptest-macro, and state-machine</li>
<li><a href=""><code>a85563f</code></a> Merge pull request <a href="">#584</a> from wojciech-graj/main</li>
<li><a href=""><code>5331517</code></a> Merge pull request <a href="">#596</a> from alexanderkjall/fix-arithmetic-overflow</li>
<li><a href=""><code>157f3c0</code></a> Merge pull request <a href="">#595</a> from ebegumisa/main</li>
<li><a href=""><code>02fa1fc</code></a> changelog: add <a href="">#595</a></li>
<li><a href=""><code>27fd76f</code></a> fix for 32 bit processors</li>
<li><a href=""><code>d1716ca</code></a> Add <code>ReferenceStateMachine</code> arg to <code>SystemUnderTest::teardown</code></li>
<li><a href=""><code>ea4ddeb</code></a> Merge pull request <a href="">#594</a> from proptest-rs/attr-macro-preserve-arg-names</li>
<li><a href=""><code>f80c1e6</code></a> fix shorthand struct initialization lint</li>
<li><a href=""><code>b7590fa</code></a> add new test for complex patterns</li>
<li>Additional commits viewable in <a href="https://github.com/proptest-rs/proptest/compare/v1.7.0...v1.8.0">compare view</a></li>
</ul>
</details>
<br />

Updates `tempfile` from 3.22.0 to 3.23.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/Stebalien/tempfile/blob/master/CHANGELOG.md">tempfile's changelog</a>.</em></p>
<blockquote>
<h2>3.23.0</h2>
<ul>
<li>Remove need for the &quot;nightly&quot; feature to compile with &quot;wasip2&quot;.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>fe9f4a3</code></a> chore: release v3.23.0 (<a href="">#381</a>)</li>
<li><a href=""><code>006c3fd</code></a> fix: use std::os::fd instead of std::os::wasi (<a href="">#380</a>)</li>
<li><a href=""><code>b0e6309</code></a> doc: Update COPYRIGHT link (<a href="">#377</a>)</li>
<li><a href=""><code>2d6fc3f</code></a> Fix formatting in Builder::disable_cleanup documentation (<a href="">#375</a>)</li>
<li>See full diff in <a href="https://github.com/Stebalien/tempfile/compare/v3.22.0...v3.23.0">compare view</a></li>
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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `450250eff8a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.