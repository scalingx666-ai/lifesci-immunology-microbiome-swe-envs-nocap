# Issue

**Title:** Build(deps-rs): Bump the dependencies group across 1 directory with 6 updates

## Description

Bumps the dependencies group with 6 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [histogram](https://github.com/iopsystems/histogram) | `0.11.4` | `1.0.0` |
| [needletail](https://github.com/onecodex/needletail) | `0.6.3` | `0.7.2` |
| [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust) | `4.3.0` | `4.4.1` |
| [proptest](https://github.com/proptest-rs/proptest) | `1.10.0` | `1.11.0` |
| [tempfile](https://github.com/Stebalien/tempfile) | `3.26.0` | `3.27.0` |
| [wasm-bindgen-test](https://github.com/wasm-bindgen/wasm-bindgen) | `0.3.64` | `0.3.67` |

Updates `histogram` from 0.11.4 to 1.0.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/releases">histogram's releases</a>.</em></p>
<blockquote>
<h2>v1.0.0</h2>
<h2>What's Changed</h2>
<ul>
<li>release: v1.0.0 by <a href="https://github.com/brayniac"><code>@​brayniac</code></a> in <a href="">iopsystems/histogram#1</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/brayniac"><code>@​brayniac</code></a> made their first contribution in <a href="">iopsystems/histogram#1</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/iopsystems/histogram/commits/v1.0.0">https://github.com/iopsystems/histogram/commits/v1.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/blob/main/CHANGELOG.md">histogram's changelog</a>.</em></p>
<blockquote>
<h2>[1.0.0] - 2026-03-20</h2>
<p>First release with changelog.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/iopsystems/histogram/commits/v1.0.0">compare view</a></li>
</ul>
</details>
<br />

Updates `needletail` from 0.6.3 to 0.7.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/onecodex/needletail/releases">needletail's releases</a>.</em></p>
<blockquote>
<h2>v0.7.2</h2>
<h2>What's Changed</h2>
<ul>
<li>Update <code>Record</code> signature in the Python module by <a href="https://github.com/apcamargo"><code>@​apcamargo</code></a> in <a href="">onecodex/needletail#112</a></li>
<li>Add NeedletailError to stub file by <a href="https://github.com/audy"><code>@​audy</code></a> in <a href="">onecodex/needletail#113</a></li>
<li>Fix typos by <a href="https://github.com/mo8it"><code>@​mo8it</code></a> in <a href="">onecodex/needletail#76</a></li>
<li>Bump bzip2 to 0.6 for new rust backend by <a href="https://github.com/RagnarGrootKoerkamp"><code>@​RagnarGrootKoerkamp</code></a> in <a href="">onecodex/needletail#115</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/RagnarGrootKoerkamp"><code>@​RagnarGrootKoerkamp</code></a> made their first contribution in <a href="">onecodex/needletail#115</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/onecodex/needletail/compare/v0.7.1...v0.7.2">https://github.com/onecodex/needletail/compare/v0.7.1...v0.7.2</a></p>
<h2>v0.7.1</h2>
<h3>Added</h3>
<ul>
<li>Build Python 3.14 wheels (<a href="">#109</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Add missing <code>id</code>, <code>seq</code>, and <code>qual</code> attributes of the <code>Record</code> class to the Python stub file (<a href="">#106</a>)</li>
<li>Fix multiline comment in <code>python.rs</code> module (<a href="">#107</a>)</li>
</ul>
<p>Thanks <a href="https://github.com/apcamargo"><code>@​apcamargo</code></a>! 🎉</p>
<h2>v0.7.0</h2>
<h2>Added</h2>
<ul>
<li>Add the <code>phred_quality_score</code> method to the Python <code>Record</code> class (<a href="">#98</a>)</li>
<li>Add Phred decoding functionality (<a href="">#102</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0e4e86d</code></a> Bump to v0.7.2</li>
<li><a href=""><code>e17e300</code></a> Bump bzip2 to 0.6 for new rust backend (<a href="">#115</a>)</li>
<li><a href=""><code>c57930a</code></a> lint</li>
<li><a href=""><code>1e2d736</code></a> Fix typos (<a href="">#76</a>)</li>
<li><a href=""><code>b30764f</code></a> Add NeedletailError to stub file (<a href="">#113</a>)</li>
<li><a href=""><code>3505aa7</code></a> Update <code>Record</code> signature (<a href="">#112</a>)</li>
<li><a href=""><code>85c18b5</code></a> Bump to 0.7.1 (<a href="">#110</a>)</li>
<li><a href=""><code>bfaceee</code></a> Build for Python 3.14 (<a href="">#109</a>)</li>
<li><a href=""><code>a7daa6c</code></a> Fix multiline comment in the <code>python.rs</code> module (<a href="">#107</a>)</li>
<li><a href=""><code>dd6c276</code></a> Include attributes in the stub file (<a href="">#106</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/onecodex/needletail/compare/v0.6.3...v0.7.2">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 4.3.0 to 4.4.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v4.4.1</h2>
<h2>What's changed</h2>
<ul>
<li>chore: update documentation URLs and reformat Cargo.toml files, by <a href="https://github.com/adriencaccia"><code>@​adriencaccia</code></a> (<a href="">378d5f8</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.4.0...v4.4.1">https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.4.0...v4.4.1</a></p>
<h2>v4.4.0</h2>
<h2>What's Changed</h2>
<ul>
<li>feat(cargo-codspeed): allow build with multiple modes by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#162</a></li>
<li>chore(deps): update rust crate nix to 0.31.2 by <a href="https://github.com/xtqqczze"><code>@​xtqqczze</code></a> in <a href="">CodSpeedHQ/codspeed-rust#167</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/xtqqczze"><code>@​xtqqczze</code></a> made their first contribution in <a href="">CodSpeedHQ/codspeed-rust#167</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.3.0...v4.4.0">https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.3.0...v4.4.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dccf5f4</code></a> Release 4.4.1</li>
<li><a href=""><code>378d5f8</code></a> chore: update documentation URLs and reformat Cargo.toml files</li>
<li><a href=""><code>163ca0d</code></a> Release 4.4.0</li>
<li><a href=""><code>49ad41e</code></a> chore(deps): update rust crate nix to 0.31.2 (<a href="">#167</a>)</li>
<li><a href=""><code>7fc87c3</code></a> feat(cargo-codspeed): allow build with multiple modes</li>
<li>See full diff in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.3.0...v4.4.1">compare view</a></li>
</ul>
</details>
<br />

Updates `proptest` from 1.10.0 to 1.11.0
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7f1367f</code></a> Merge pull request <a href="">#641</a> from proptest-rs/release-1.11</li>
<li><a href=""><code>a63bf7e</code></a> proptest-state-machine v0.8.0</li>
<li><a href=""><code>d86e9ff</code></a> add changelog for <a href="">#640</a></li>
<li><a href=""><code>7940313</code></a> proptest v1.11.0</li>
<li><a href=""><code>3ec998c</code></a> fix <a href="">#638</a> changelog</li>
<li><a href=""><code>8ceb00c</code></a> Merge pull request <a href="">#639</a> from lukoktonos/bits128</li>
<li><a href=""><code>9c8df1a</code></a> Merge pull request <a href="">#638</a> from folkertdev/f16-support</li>
<li><a href=""><code>ca9d8e1</code></a> changelog <a href="">#638</a></li>
<li><a href=""><code>a39869f</code></a> imply f16 feat by unstable</li>
<li><a href=""><code>85c5ca0</code></a> Merge pull request <a href="">#637</a> from folkertdev/min-max-assoc-constants</li>
<li>Additional commits viewable in <a href="https://github.com/proptest-rs/proptest/compare/v1.10.0...v1.11.0">compare view</a></li>
</ul>
</details>
<br />

Updates `tempfile` from 3.26.0 to 3.27.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/Stebalien/tempfile/blob/master/CHANGELOG.md">tempfile's changelog</a>.</em></p>
<blockquote>
<h2>3.27.0</h2>
<p>This release adds <code>TempPath::try_from_path</code> and deprecates <code>TempPath::from_path</code>.</p>
<p>Prior to this release, <code>TempPath::from_path</code> made no attempts to convert relative paths into absolute paths. The following code would have deleted the wrong file:</p>
<pre lang="rust"><code>let tmp_path = TempPath::from_path(&quot;foo&quot;)
std::env::set_current_dir(&quot;/some/other/path&quot;).unwrap();
drop(tmp_path);
</code></pre>
<p>Now:</p>
<ol>
<li><code>TempPath::from_path</code> will attempt to convert relative paths into absolute paths. However, this isn't always possible as we need to call <code>std::env::current_dir</code>, which can fail. If we fail to convert the relative path to an absolute path, we simply keep the relative path.</li>
<li>The <code>TempPath::try_from_path</code> behaves exactly like <code>TempPath::from_path</code>, except that it returns an error if we fail to convert a relative path into an absolute path (or if the passed path is empty).</li>
</ol>
<p>Neither function attempt to verify the existence of the file in question.</p>
<p>Thanks to <a href="https://github.com/meng-xu-cs"><code>@​meng-xu-cs</code></a> for reporting this issue.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5c8fa12</code></a> chore: release 3.27.0</li>
<li><a href=""><code>e34e574</code></a> test: disable uds conflict test on redox</li>
<li><a href=""><code>772c795</code></a> test: add CWD guards</li>
<li><a href=""><code>2632fb9</code></a> fix: resolve relative paths when constructing <code>TempPath</code></li>
<li>See full diff in <a href="https://github.com/Stebalien/tempfile/compare/v3.26.0...v3.27.0">compare view</a></li>
</ul>
</details>
<br />

Updates `wasm-bindgen-test` from 0.3.64 to 0.3.67
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/wasm-bindgen/wasm-bindgen/commits">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `500ec9768357`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.