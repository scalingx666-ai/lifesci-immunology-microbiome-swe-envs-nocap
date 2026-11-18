# Issue

**Title:** Build(deps-py): Update maturin requirement from <1.13.0,>=1 to >=1,<1.14.0 in the dependencies group across 1 directory

## Description

Updates the requirements on [maturin](https://github.com/pyo3/maturin) to permit the latest version.
Updates `maturin` to 1.13.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pyo3/maturin/releases">maturin's releases</a>.</em></p>
<blockquote>
<h2>v1.13.1</h2>
<h2>What's Changed</h2>
<ul>
<li>fix: fall back to placeholder for abi3 when found interpreters are too old by <a href="https://github.com/messense"><code>@​messense</code></a> in <a href="">PyO3/maturin#3126</a></li>
</ul>
<p>See also v1.13.0 release highlight: <a href="https://github.com/PyO3/maturin/releases/tag/v1.13.0">https://github.com/PyO3/maturin/releases/tag/v1.13.0</a></p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/PyO3/maturin/compare/v1.13.0...v1.13.1">https://github.com/PyO3/maturin/compare/v1.13.0...v1.13.1</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyO3/maturin/blob/main/Changelog.md">maturin's changelog</a>.</em></p>
<blockquote>
<h1>Changelog</h1>
<h2>1.13.0</h2>
<ul>
<li>Fix: fall back to placeholder for abi3 when found interpreters are too old (<a href="">#3126</a>)</li>
</ul>
<h2>1.13.0</h2>
<ul>
<li>Refactor: unified interpreter resolution pipeline (<a href="">#3032</a>)</li>
<li>Refactor: decompose large modules into focused submodules (<a href="">#3052</a>)</li>
<li>Keep cargo build artifact at original path after staging (<a href="">#3054</a>)</li>
<li>Fix <code>--strip</code> conflicting with <code>--include-debuginfo</code> in develop (<a href="">#3057</a>)</li>
<li>Fix abi3 wheel producing version-specific tags for CPython below minimum (<a href="">#3061</a>)</li>
<li>Generate-ci: use uv pip for pytest steps to fix local wheel preference (<a href="">#3063</a>)</li>
<li>Update reflink-copy to 0.1.29 to fix sparc Linux builds</li>
<li>Add <code>[tool.maturin.generate-ci.github]</code> config support (<a href="">#3066</a>)</li>
<li>Fix(sdist): handle parent workspaces and refactor sdist generation (<a href="">#3055</a>)</li>
<li>Test: refactor integration suite and switch mixed fixtures to cffi (<a href="">#3068</a>)</li>
<li>Fix <code>data</code> symlink permission handling (<a href="">#3069</a>)</li>
<li>Fix: correct bugs in audit.rs typo and module_writer (<a href="">#3070</a>)</li>
<li>Perf: use lazy-initialized regexes instead of per-call compilation (<a href="">#3071</a>)</li>
<li>Refactor: extract duplicated helpers and reduce code repetition (<a href="">#3072</a>)</li>
<li>Refactor: split monster functions into focused methods (<a href="">#3073</a>)</li>
<li>Refactor: improve type safety and API clarity (<a href="">#3074</a>)</li>
<li>Refactor: cleanup anti-patterns (<a href="">#3075</a>)</li>
<li>Refactor: decompose <code>build_context</code> into focused submodules (<a href="">#3076</a>)</li>
<li>Fix: skip legacy manylinux aliases not in PyPI allow-list (<a href="">#3078</a>)</li>
<li>Fix: auto-generate <code>.def</code> file for zig + windows-gnu to export <code>PyInit</code> symbol (<a href="">#3079</a>)</li>
<li>Ci: upgrade run-on-arch-action to ubuntu24.04, add deadsnakes PPA for newer Python (<a href="">#3081</a>)</li>
<li>Fix: pass <code>-undefined dynamic_lookup</code> via <code>CARGO_ENCODED_RUSTFLAGS</code> on macOS (<a href="">#3083</a>)</li>
<li>Feat: add Profile-Guided Optimization (PGO) support (<a href="">#3085</a>)</li>
<li>Respect <code>metadata_directory</code> in <code>build_wheel</code> per PEP 517 (<a href="">#3086</a>)</li>
<li>Update lddtree to 0.5.0</li>
<li>Fix cargo path with puccinialin for Windows (<a href="">#3093</a>)</li>
<li>Update and pin cargo-cyclonedx to 0.5.9</li>
<li>Ci: improve GitHub Actions generation logic (<a href="">#3097</a>)</li>
<li>Refactor: split BuildOptions and BuildContext into logical sub-groups (<a href="">#3098</a>)</li>
<li>Refactor: move subcommands to separate modules (<a href="">#3099</a>)</li>
<li>Refactor: decouple build orchestration from BuildContext (<a href="">#3100</a>)</li>
<li>Upgrade pyo3 to 0.28 (<a href="">#3101</a>)</li>
<li>Fix: only enable include_debuginfo by default on Windows in develop command</li>
<li>PyO3: Adds <code>--generate_stubs</code> build options (<a href="">#3105</a>)</li>
<li>Fix: prevent panic when no interpreters match abi3 minimum version (<a href="">#3108</a>)</li>
<li>Refactor to store CPython ABI metadata in a struct combining two enums (<a href="">#3110</a>)</li>
<li>Refactor: introduce <code>WheelRepairer</code> trait (<a href="">#3112</a>)</li>
<li>Feat: re-implement delocate for repairing macOS wheels (<a href="">#3114</a>)</li>
<li>PyO3: Adds generate-stubs command (<a href="">#3115</a>)</li>
<li>Feat: re-implement delvewheel for repairing Windows wheels (<a href="">#3116</a>)</li>
<li>Add auditwheel Warn mode, default to Warn on macOS/Windows (<a href="">#3121</a>)</li>
<li>Feat: Support large zip files (<a href="">#3118</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b27b7e1</code></a> Release v1.13.1</li>
<li><a href=""><code>4a3df46</code></a> fix: fall back to placeholder for abi3 when found interpreters are too old (#...</li>
<li><a href=""><code>e8ebb2f</code></a> Release v1.13.0 (<a href="">#3124</a>)</li>
<li><a href=""><code>1e5d362</code></a> feat: Support large zip files (<a href="">#3118</a>)</li>
<li><a href=""><code>062bea7</code></a> Add auditwheel Warn mode, default to Warn on macOS/Windows (<a href="">#3121</a>)</li>
<li><a href=""><code>70ea112</code></a> feat: re-implement delvewheel for repairing Windows wheels (<a href="">#3116</a>)</li>
<li><a href=""><code>83cb185</code></a> PyO3: Adds generate-stubs command (<a href="">#3115</a>)</li>
<li><a href=""><code>ac062c3</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#3117</a>)</li>
<li><a href=""><code>a8393eb</code></a> feat: re-implement delocate for repairing macOS wheels (<a href="">#3114</a>)</li>
<li><a href=""><code>d97bbd0</code></a> refactor: introduce <code>WheelRepairer</code> trait (<a href="">#3112</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pyo3/maturin/compare/v1.0.0...v1.13.1">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64e527f2384b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.