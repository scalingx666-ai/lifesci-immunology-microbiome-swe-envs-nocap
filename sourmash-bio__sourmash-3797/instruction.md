# Issue

**Title:** Build(deps-rs): Bump the dependencies group across 1 directory with 6 updates

## Description

Bumps the dependencies group with 6 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [camino](https://github.com/camino-rs/camino) | `1.1.10` | `1.1.11` |
| [cfg-if](https://github.com/rust-lang/cfg-if) | `1.0.1` | `1.0.3` |
| [memmap2](https://github.com/RazrFalcon/memmap2-rs) | `0.9.7` | `0.9.8` |
| [serde_json](https://github.com/serde-rs/json) | `1.0.141` | `1.0.143` |
| [thiserror](https://github.com/dtolnay/thiserror) | `2.0.12` | `2.0.16` |
| [tempfile](https://github.com/Stebalien/tempfile) | `3.20.0` | `3.21.0` |

Updates `camino` from 1.1.10 to 1.1.11
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/releases">camino's releases</a>.</em></p>
<blockquote>
<h2>camino 1.1.11</h2>
<h3>Added</h3>
<ul>
<li><code>Utf8PathBuf::leak</code> on Rust 1.89 and above.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/blob/main/CHANGELOG.md">camino's changelog</a>.</em></p>
<blockquote>
<h2>[1.1.11] - 2025-08-17</h2>
<h3>Added</h3>
<ul>
<li><code>Utf8PathBuf::leak</code> on Rust 1.89 and above.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9c904bd</code></a> [camino] version 1.1.11</li>
<li><a href=""><code>29f5064</code></a> prepare release</li>
<li><a href=""><code>3aad190</code></a> add Utf8PathBuf::leak</li>
<li><a href=""><code>fbe5d79</code></a> clippy fixes for Rust 1.89</li>
<li>See full diff in <a href="https://github.com/camino-rs/camino/compare/camino-1.1.10...camino-1.1.11">compare view</a></li>
</ul>
</details>
<br />

Updates `cfg-if` from 1.0.1 to 1.0.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/releases">cfg-if's releases</a>.</em></p>
<blockquote>
<h2>v1.0.3</h2>
<ul>
<li>Revert &quot;Remove <code>@__identity</code> rule.&quot;</li>
</ul>
<h2>v1.0.2</h2>
<ul>
<li>Remove <code>@__identity</code> rule.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/blob/main/CHANGELOG.md">cfg-if's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/rust-lang/cfg-if/compare/v1.0.2...v1.0.3">1.0.3</a> - 2025-08-19</h2>
<ul>
<li>Revert &quot;Remove <code>@__identity</code> rule.&quot;</li>
</ul>
<h2><a href="https://github.com/rust-lang/cfg-if/compare/v1.0.1...v1.0.2">1.0.2</a> - 2025-08-19</h2>
<ul>
<li>Remove <code>@__identity</code> rule.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9c7bb0b</code></a> chore: release v1.0.3 (<a href="">#93</a>)</li>
<li><a href=""><code>145894c</code></a> Revert &quot;Remove <code>@__identity</code> rule.&quot;</li>
<li><a href=""><code>9f747fe</code></a> chore: release v1.0.2 (<a href="">#88</a>)</li>
<li><a href=""><code>97739b8</code></a> Fix some ugly and inconsistent formatting.</li>
<li><a href=""><code>4d7a585</code></a> Remove <code>@__identity</code> rule.</li>
<li><a href=""><code>527acbd</code></a> Bump actions/checkout from 4 to 5</li>
<li>See full diff in <a href="https://github.com/rust-lang/cfg-if/compare/v1.0.1...v1.0.3">compare view</a></li>
</ul>
</details>
<br />

Updates `memmap2` from 0.9.7 to 0.9.8
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/RazrFalcon/memmap2-rs/blob/master/CHANGELOG.md">memmap2's changelog</a>.</em></p>
<blockquote>
<h2>[0.9.8] - 2025-08-22</h2>
<h3>Added</h3>
<ul>
<li><code>MmapOptions::no_reserve_swap</code>.
<a href="https://github.com/nhtyy"><code>@​nhtyy</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>05b2d0e</code></a> Merge pull request <a href="">#154</a> from RazrFalcon/release/v0.9.8</li>
<li><a href=""><code>b59eb44</code></a> Bump version to 0.9.8.</li>
<li><a href=""><code>2907b1e</code></a> Merge pull request <a href="">#153</a> from nhtyy/n/noreserve</li>
<li><a href=""><code>8bfe4e5</code></a> Rename noreserve in impl to no_reserve.</li>
<li><a href=""><code>3fcecb6</code></a> Also support <code>no_reserve_swap()</code> on Illumos.</li>
<li><a href=""><code>c8235d7</code></a> chore: run <code>cargo fmt</code></li>
<li><a href=""><code>beb3d3a</code></a> fix: apply suggestions to comments</li>
<li><a href=""><code>2abbcd6</code></a> fix: cfg target_os</li>
<li><a href=""><code>7b67e0d</code></a> fix: update stub and comments</li>
<li><a href=""><code>ec72e01</code></a> fix: noreserve -&gt; noreserve_swap</li>
<li>Additional commits viewable in <a href="https://github.com/RazrFalcon/memmap2-rs/compare/v0.9.7...v0.9.8">compare view</a></li>
</ul>
</details>
<br />

Updates `serde_json` from 1.0.141 to 1.0.143
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.143</h2>
<ul>
<li>Implement Clone and Debug for serde_json::Map iterators (<a href="">#1264</a>, thanks <a href="https://github.com/xlambein"><code>@​xlambein</code></a>)</li>
<li>Implement Default for CompactFormatter (<a href="">#1268</a>, thanks <a href="https://github.com/SOF3"><code>@​SOF3</code></a>)</li>
<li>Implement FromStr for serde_json::Map (<a href="">#1271</a>, thanks <a href="https://github.com/mickvangelderen"><code>@​mickvangelderen</code></a>)</li>
</ul>
<h2>v1.0.142</h2>
<ul>
<li>impl Default for &amp;Value (<a href="">#1265</a>, thanks <a href="https://github.com/aatifsyed"><code>@​aatifsyed</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>10102c4</code></a> Release 1.0.143</li>
<li><a href=""><code>2a5b853</code></a> Replace super::super with absolute path within crate</li>
<li><a href=""><code>447170b</code></a> Merge pull request 1271 from mickvangelderen/mick/impl-from-str-for-map</li>
<li><a href=""><code>ec190d6</code></a> Merge pull request <a href="">#1264</a> from xlambein/master</li>
<li><a href=""><code>8be6647</code></a> Merge pull request <a href="">#1268</a> from SOF3/compact-default</li>
<li><a href=""><code>ba5b3cc</code></a> Revert &quot;Pin nightly toolchain used for miri job&quot;</li>
<li><a href=""><code>1731167</code></a> Release 1.0.142</li>
<li><a href=""><code>e51c814</code></a> Touch up PR 1265</li>
<li><a href=""><code>84abbdb</code></a> Merge pull request <a href="">#1265</a> from aatifsyed/master</li>
<li><a href=""><code>fd35a02</code></a> Implement FromStr for Map&lt;String, Value&gt;</li>
<li>Additional commits viewable in <a href="https://github.com/serde-rs/json/compare/v1.0.141...v1.0.143">compare view</a></li>
</ul>
</details>
<br />

Updates `thiserror` from 2.0.12 to 2.0.16
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/dtolnay/thiserror/releases">thiserror's releases</a>.</em></p>
<blockquote>
<h2>2.0.16</h2>
<ul>
<li>Add to &quot;no-std&quot; crates.io category (<a href="">#429</a>)</li>
</ul>
<h2>2.0.15</h2>
<ul>
<li>Prevent <code>Error::provide</code> API becoming unavailable from a future new compiler lint (<a href="">#427</a>)</li>
</ul>
<h2>2.0.14</h2>
<ul>
<li>Allow build-script cleanup failure with NFSv3 output directory to be non-fatal (<a href="">#426</a>)</li>
</ul>
<h2>2.0.13</h2>
<ul>
<li>Documentation improvements</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>40b5853</code></a> Release 2.0.16</li>
<li><a href=""><code>83dfb5f</code></a> Merge pull request <a href="">#429</a> from dtolnay/nostd</li>
<li><a href=""><code>9b4a99f</code></a> Add to &quot;no-std&quot; crates.io category</li>
<li><a href=""><code>f6145eb</code></a> Release 2.0.15</li>
<li><a href=""><code>2717177</code></a> Merge pull request <a href="">#427</a> from dtolnay/caplints</li>
<li><a href=""><code>2cd13e6</code></a> Make error_generic_member_access compatible with -Dwarnings</li>
<li><a href=""><code>eea6799</code></a> Release 2.0.14</li>
<li><a href=""><code>a2aa6d7</code></a> Merge pull request <a href="">#426</a> from dtolnay/enotempty</li>
<li><a href=""><code>f00ebc5</code></a> Allow build-script cleanup failure with NFSv3 output directory to be non-fatal</li>
<li><a href=""><code>61f28da</code></a> Release 2.0.13</li>
<li>Additional commits viewable in <a href="https://github.com/dtolnay/thiserror/compare/2.0.12...2.0.16">compare view</a></li>
</ul>
</details>
<br />

Updates `tempfile` from 3.20.0 to 3.21.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/Stebalien/tempfile/blob/master/CHANGELOG.md">tempfile's changelog</a>.</em></p>
<blockquote>
<h2>3.21.0</h2>
<ul>
<li>Updated <code>windows-sys</code> requirement to allow version 0.60.x</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>48bff5f</code></a> test(tempdir): configure tempdir on wasi</li>
<li><a href=""><code>704a1d2</code></a> test(tempdir): cleanup tempdir tests and run more tests on wasi</li>
<li><a href=""><code>a0dc80d</code></a> Add Android CI target  (<a href="">#367</a>)</li>
<li><a href=""><code>4ad1ae6</code></a> chore(release): release 3.21.0</li>
<li><a href=""><code>3849edd</code></a> build(deps): bump actions/checkout from 4 to 5 (<a href="">#368</a>)</li>
<li><a href=""><code>0657fdf</code></a> build(deps): update windows-sys requirement &lt;0.61 (<a href="">#360</a>)</li>
<li><a href=""><code>69b95c7</code></a> ci: fix was tests in CI (<a href="">#361</a>)</li>
<li>See full diff in <a href="https://github.com/Stebalien/tempfile/compare/v3.20.0...v3.21.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a5b4b5ccabb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.