# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [camino](https://github.com/camino-rs/camino) and [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust).

Updates `camino` from 1.2.3 to 1.2.4
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/releases">camino's releases</a>.</em></p>
<blockquote>
<h2>camino 1.2.4</h2>
<h3>Added</h3>
<p>Methods to convert between <code>Box&lt;Utf8Path&gt;</code> and <code>Box&lt;Path&gt;</code>:</p>
<ul>
<li><code>From&lt;Box&lt;Utf8Path&gt;&gt; for Box&lt;Path&gt;</code> (as of release, not documented due to <a href="">rust-lang/rust#158466</a>).</li>
<li><code>Utf8Path::into_std_boxed_path(self: Box&lt;Self&gt;)</code></li>
<li><code>Utf8Path::from_boxed_path(path: Box&lt;Path&gt;)</code></li>
<li><code>TryFrom&lt;Box&lt;Path&gt;&gt; for Box&lt;Utf8Path&gt;</code></li>
</ul>
<p>Thanks <a href="https://github.com/nicopap">nicopap</a> for your first contribution!</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/blob/main/CHANGELOG.md">camino's changelog</a>.</em></p>
<blockquote>
<h2>[1.2.4] - 2026-06-27</h2>
<h3>Added</h3>
<p>Methods to convert between <code>Box&lt;Utf8Path&gt;</code> and <code>Box&lt;Path&gt;</code>:</p>
<ul>
<li><code>From&lt;Box&lt;Utf8Path&gt;&gt; for Box&lt;Path&gt;</code> (as of release, not documented due to <a href="">rust-lang/rust#158466</a>).</li>
<li><code>Utf8Path::into_std_boxed_path(self: Box&lt;Self&gt;)</code></li>
<li><code>Utf8Path::from_boxed_path(path: Box&lt;Path&gt;)</code></li>
<li><code>TryFrom&lt;Box&lt;Path&gt;&gt; for Box&lt;Utf8Path&gt;</code></li>
</ul>
<p>Thanks <a href="https://github.com/nicopap">nicopap</a> for your first contribution!</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8966366</code></a> [camino] version 1.2.4</li>
<li><a href=""><code>abf526b</code></a> [meta] prepare release</li>
<li><a href=""><code>417c6e1</code></a> docs: fix dangling [from] link in into_std_boxed_path (<a href="">#125</a>)</li>
<li><a href=""><code>6d25706</code></a> add Box&lt;Path&gt; -&gt; Box&lt;Utf8Path&gt; conversion (<a href="">#124</a>)</li>
<li><a href=""><code>816ddeb</code></a> test <code>Box\&lt;Utf8Path&gt;</code> conversions, and other review fixes (<a href="">#123</a>)</li>
<li><a href=""><code>e437cc3</code></a> Add conversion from Box&lt;Utf8Path&gt; to Box&lt;Path&gt; (<a href="">#122</a>)</li>
<li>See full diff in <a href="https://github.com/camino-rs/camino/compare/camino-1.2.3...camino-1.2.4">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 4.7.0 to 5.0.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v5.0.1</h2>
<h2>What's Changed</h2>
<ul>
<li>fix(divan): bump proc-macro-crate to parse multiline inline tables by <a href="https://github.com/GuillaumeLagrange"><code>@​GuillaumeLagrange</code></a> in <a href="">CodSpeedHQ/codspeed-rust#185</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.0...v5.0.1">https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.0...v5.0.1</a></p>
<h2>v5.0.0</h2>
<h2>💥 BREAKING</h2>
<p>MSRV bumped to 1.85 for all packages: <code>codspeed</code>, <code>codspeed-criterion-compat</code>, <code>codspeed-divan-compat</code></p>
<h2>What's Changed</h2>
<p>This release includes a fix for benchmark URI generation when users do not use the provided macros to declare their criterion main function.</p>
<ul>
<li>fix(criterion-compat): fix URI formatting when criterion_group!/criterion_main! are bypassed by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#169</a></li>
<li>Fix lower bound of cc crate by <a href="https://github.com/konstin"><code>@​konstin</code></a> in <a href="">CodSpeedHQ/codspeed-rust#182</a></li>
<li>Update colored dep by <a href="https://github.com/rukai"><code>@​rukai</code></a> in <a href="">CodSpeedHQ/codspeed-rust#142</a></li>
<li>update getrandom to 0.4 by <a href="https://github.com/Ludea"><code>@​Ludea</code></a> in <a href="">CodSpeedHQ/codspeed-rust#177</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/rukai"><code>@​rukai</code></a> made their first contribution in <a href="">CodSpeedHQ/codspeed-rust#142</a></li>
<li><a href="https://github.com/Ludea"><code>@​Ludea</code></a> made their first contribution in <a href="">CodSpeedHQ/codspeed-rust#177</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.7.0...v5.0.0">https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.7.0...v5.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>69f74b6</code></a> Release 5.0.1</li>
<li><a href=""><code>9229680</code></a> fix(divan): bump proc-macro-crate to parse multiline inline tables</li>
<li><a href=""><code>9339a52</code></a> Release 5.0.0</li>
<li><a href=""><code>b79f040</code></a> chore: bump repo toolchain to 1.96</li>
<li><a href=""><code>c42d392</code></a> chore: update getrandom to 0.4</li>
<li><a href=""><code>7370bbf</code></a> chore!: bump MSRV to 1.85</li>
<li><a href=""><code>b30ce7d</code></a> chore!: update colored dep</li>
<li><a href=""><code>d854488</code></a> chore!: bump MSRV to 1.80</li>
<li><a href=""><code>73170f9</code></a> Fix lower bound of cc crate (<a href="">#182</a>)</li>
<li><a href=""><code>ec46807</code></a> test(criterion_compat): add custom main bench for URI formatting</li>
<li>Additional commits viewable in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.7.0...v5.0.1">compare view</a></li>
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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e8ebaca22b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.