# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 4 updates

## Description

Bumps the dependencies group with 4 updates: [camino](https://github.com/camino-rs/camino), [serde](https://github.com/serde-rs/serde), [serde_json](https://github.com/serde-rs/json) and [tempfile](https://github.com/Stebalien/tempfile).

Updates `camino` from 1.1.12 to 1.2.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/releases">camino's releases</a>.</em></p>
<blockquote>
<h2>camino 1.2.0</h2>
<h3>Changed</h3>
<ul>
<li>MSRV updated to Rust 1.61 to support the switch to <code>serde_core</code>.</li>
<li>camino now depends on <code>serde_core</code> rather than <code>serde</code>. This allows camino's compilation to be parallelized with <code>serde_derive</code>.</li>
<li><code>serde</code> and <code>proptest</code> are no longer available as features. This is technically a breaking change, but these features were already no-ops. Instead, use <code>serde1</code> and <code>proptest1</code> respectively.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/blob/main/CHANGELOG.md">camino's changelog</a>.</em></p>
<blockquote>
<h2>[1.2.0] - 2025-09-14</h2>
<h3>Changed</h3>
<ul>
<li>MSRV updated to Rust 1.61 to support the switch to <code>serde_core</code>.</li>
<li>camino now depends on <code>serde_core</code> rather than <code>serde</code>. This allows camino's compilation to be parallelized with <code>serde_derive</code>.</li>
<li><code>serde</code> and <code>proptest</code> are no longer available as features. This is technically a breaking change, but these features were already no-ops. Instead, use <code>serde1</code> and <code>proptest1</code> respectively.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>62ddbaa</code></a> [camino] version 1.2.0</li>
<li><a href=""><code>b525ad9</code></a> changelog + minor doc updates</li>
<li><a href=""><code>0150dc9</code></a> switch to serde_core</li>
<li><a href=""><code>a2a7da0</code></a> switch to dep: for optional dependencies</li>
<li><a href=""><code>f16b48f</code></a> update edition to 2021</li>
<li><a href=""><code>8540bc3</code></a> update MSRV to Rust 1.61</li>
<li><a href=""><code>2d6994c</code></a> add changelog link</li>
<li>See full diff in <a href="https://github.com/camino-rs/camino/compare/camino-1.1.12...camino-1.2.0">compare view</a></li>
</ul>
</details>
<br />

Updates `serde` from 1.0.219 to 1.0.224
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/serde/releases">serde's releases</a>.</em></p>
<blockquote>
<h2>v1.0.224</h2>
<ul>
<li>Remove private types being suggested in rustc diagnostics (<a href="">#2979</a>)</li>
</ul>
<h2>v1.0.223</h2>
<ul>
<li>Fix serde_core documentation links (<a href="">#2978</a>)</li>
</ul>
<h2>v1.0.222</h2>
<ul>
<li>Make <code>serialize_with</code> attribute produce code that works if respanned to 2024 edition (<a href="">#2950</a>, thanks <a href="https://github.com/aytey"><code>@​aytey</code></a>)</li>
</ul>
<h2>v1.0.221</h2>
<ul>
<li>Documentation improvements (<a href="">#2973</a>)</li>
<li>Deprecate <code>serde_if_integer128!</code> macro (<a href="">#2975</a>)</li>
</ul>
<h2>v1.0.220</h2>
<ul>
<li>Add a way for data formats to depend on serde traits without waiting for serde_derive compilation: <a href="https://docs.rs/serde_core">https://docs.rs/serde_core</a> (<a href="">#2608</a>, thanks <a href="https://github.com/osiewicz"><code>@​osiewicz</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1699882</code></a> Release 1.0.224</li>
<li><a href=""><code>840f6ec</code></a> Merge pull request <a href="">#2979</a> from dtolnay/private</li>
<li><a href=""><code>bf9ebea</code></a> Mark every trait impl for a private type with do_not_recommend</li>
<li><a href=""><code>6c316d7</code></a> Release 1.0.223</li>
<li><a href=""><code>a4ac0c2</code></a> Merge pull request <a href="">#2978</a> from dtolnay/htmlrooturl</li>
<li><a href=""><code>ed76364</code></a> Change serde_core's html_root_url to docs.rs/serde_core</li>
<li><a href=""><code>57e21a1</code></a> Release 1.0.222</li>
<li><a href=""><code>bb58726</code></a> Merge pull request <a href="">#2950</a> from aytey/fix_lifetime_issue_2024</li>
<li><a href=""><code>3f69251</code></a> Delete unneeded field of MapDeserializer</li>
<li><a href=""><code>fd4decf</code></a> Merge pull request <a href="">#2976</a> from dtolnay/content</li>
<li>Additional commits viewable in <a href="https://github.com/serde-rs/serde/compare/v1.0.219...v1.0.224">compare view</a></li>
</ul>
</details>
<br />

Updates `serde_json` from 1.0.143 to 1.0.145
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.145</h2>
<ul>
<li>Raise serde version requirement to &gt;=1.0.220</li>
</ul>
<h2>v1.0.144</h2>
<ul>
<li>Switch serde dependency to serde_core (<a href="">#1285</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>efa66e3</code></a> Release 1.0.145</li>
<li><a href=""><code>23679e2</code></a> Add serde version constraint</li>
<li><a href=""><code>fc27baf</code></a> Release 1.0.144</li>
<li><a href=""><code>caef3c6</code></a> Ignore uninlined_format_args pedantic clippy lint</li>
<li><a href=""><code>81ba3aa</code></a> Merge pull request <a href="">#1285</a> from dtolnay/serdecore</li>
<li><a href=""><code>d21e8ce</code></a> Switch serde dependency to serde_core</li>
<li><a href=""><code>6beb6cd</code></a> Merge pull request <a href="">#1286</a> from dtolnay/up</li>
<li><a href=""><code>1dbc803</code></a> Raise required compiler to Rust 1.61</li>
<li><a href=""><code>0bf5d87</code></a> Enforce trybuild &gt;= 1.0.108</li>
<li><a href=""><code>d12e943</code></a> Update actions/checkout@v4 -&gt; v5</li>
<li>See full diff in <a href="https://github.com/serde-rs/json/compare/v1.0.143...v1.0.145">compare view</a></li>
</ul>
</details>
<br />

Updates `tempfile` from 3.21.0 to 3.22.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/Stebalien/tempfile/blob/master/CHANGELOG.md">tempfile's changelog</a>.</em></p>
<blockquote>
<h2>3.22.0</h2>
<ul>
<li>Updated <code>windows-sys</code> requirement to allow version 0.61.x</li>
<li>Remove <code>unstable-windows-keep-open-tempfile</code> feature.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f720dbe</code></a> chore: release 3.22.0</li>
<li><a href=""><code>55d742c</code></a> chore: remove deprecated unstable feature flag</li>
<li><a href=""><code>bc41a0b</code></a> build(deps): update windows-sys requirement from &gt;=0.52, &lt;0.61 to &gt;=0.52, &lt;0....</li>
<li><a href=""><code>3c55387</code></a> test: make sure we don't drop tempdirs early (<a href="">#373</a>)</li>
<li><a href=""><code>17bf644</code></a> doc(builder): clarify permissions (<a href="">#372</a>)</li>
<li><a href=""><code>c7423f1</code></a> doc(env): document the alternative to setting the tempdir (<a href="">#371</a>)</li>
<li><a href=""><code>5af60ca</code></a> test(wasi): run a few tests that shouldn't have been disabled (<a href="">#370</a>)</li>
<li><a href=""><code>6c0c561</code></a> fix(doc): temp_dir doesn't check if writable</li>
<li>See full diff in <a href="https://github.com/Stebalien/tempfile/compare/v3.21.0...v3.22.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d5b9f95de1f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.