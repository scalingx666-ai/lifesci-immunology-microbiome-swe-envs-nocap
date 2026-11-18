# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 3 updates

## Description

Bumps the dependencies group with 3 updates: [histogram](https://github.com/iopsystems/histogram), [niffler](https://github.com/luizirber/niffler) and [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust).

Updates `histogram` from 1.2.0 to 1.3.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/releases">histogram's releases</a>.</em></p>
<blockquote>
<h2>v1.3.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Plan: borrowed-view types for zero-allocation percentile queries by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#16</a></li>
<li>release: v1.3.1 by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#17</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/iopsystems/histogram/compare/v1.3.0...v1.3.1">https://github.com/iopsystems/histogram/compare/v1.3.0...v1.3.1</a></p>
<h2>v1.3.0</h2>
<h2>What's Changed</h2>
<ul>
<li>Add Notebook Kit site for h2histogram.org (alternative to <a href="">#10</a>) by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#11</a></li>
<li>Add u32 bucket counts as named sibling types by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#12</a></li>
<li>Add GitHub repo link to h2histogram site TOC by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#13</a></li>
<li>Add rezolus_memory example, comparing Histogram vs sparse memory footprint by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#14</a></li>
<li>release: v1.3.0 by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#15</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/iopsystems/histogram/compare/v1.2.0...v1.3.0">https://github.com/iopsystems/histogram/compare/v1.2.0...v1.3.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/blob/main/CHANGELOG.md">histogram's changelog</a>.</em></p>
<blockquote>
<h2>[1.3.1] - 2026-04-29</h2>
<h3>Added</h3>
<ul>
<li><code>CumulativeROHistogramRef&lt;'a&gt;</code> / <code>CumulativeROHistogram32Ref&lt;'a&gt;</code> and
<code>SparseHistogramRef&lt;'a&gt;</code> / <code>SparseHistogram32Ref&lt;'a&gt;</code> — borrowed views over
histogram storage that mirror the read-only API surface of the owned types.
Lets columnar consumers compute quantiles directly off <code>&amp;[u32]</code> slices
without per-snapshot allocation or revalidation.</li>
<li><code>from_parts_unchecked</code> constructor on each ref type for hot-path use where
invariants are already known to hold; <code>from_parts</code> validates as before.</li>
<li><code>as_ref()</code> on <code>CumulativeROHistogram*</code> and <code>SparseHistogram*</code> returning the
matching ref view; <code>From&lt;&amp;Owned&gt; for OwnedRef&lt;'_&gt;</code> for trait-based conversion.</li>
<li><code>SampleQuantiles</code> impl on each ref type.</li>
</ul>
<h2>[1.3.0] - 2026-04-29</h2>
<h3>Added</h3>
<ul>
<li><code>Histogram32</code>, <code>AtomicHistogram32</code>, <code>SparseHistogram32</code>, and
<code>CumulativeROHistogram32</code> — u32-counter sibling types for all four histogram
variants, generated from shared declarative macros</li>
<li>Sealed <code>Count</code> and <code>AtomicCount</code> traits abstracting the bucket counter width
(implemented for <code>u32</code>/<code>u64</code> and their atomic counterparts)</li>
<li>Cross-width widening <code>From</code> conversions (u32 → u64) for all four histogram
families</li>
<li>Cross-width narrowing <code>TryFrom</code> conversions (u64 → u32) for <code>Histogram</code>,
<code>SparseHistogram</code>, and <code>CumulativeROHistogram</code></li>
<li>Cross-variant + narrowing <code>TryFrom</code> paths for the snapshot pipeline:
<code>Histogram</code> → <code>CumulativeROHistogram32</code>, <code>Histogram</code> → <code>SparseHistogram32</code>,
and <code>SparseHistogram</code> → <code>CumulativeROHistogram32</code></li>
<li>u32 benchmark cases for <code>Histogram</code> and <code>AtomicHistogram</code></li>
<li><code>rezolus_memory</code> example comparing <code>Histogram</code>, <code>SparseHistogram</code>, and
<code>CumulativeROHistogram</code> memory footprints from Rezolus parquet recordings</li>
<li>README &quot;Counter Width&quot; and &quot;Recommended Pipeline&quot; sections, with matching
rustdoc in <code>lib.rs</code></li>
</ul>
<h3>Changed</h3>
<ul>
<li><code>CumulativeROHistogram</code> cache-line threshold for linear-vs-binary search is
now count-type-dependent (<code>64 / size_of::&lt;C&gt;()</code>); <code>total_count</code> and
<code>individual_count</code> continue to return <code>u64</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7fb67e5</code></a> release: v1.3.1 (<a href="">#17</a>)</li>
<li><a href=""><code>9fb729c</code></a> Plan: borrowed-view types for zero-allocation percentile queries (<a href="">#16</a>)</li>
<li><a href=""><code>edb5877</code></a> release: v1.3.0 (<a href="">#15</a>)</li>
<li><a href=""><code>4663598</code></a> Add rezolus_memory example, comparing Histogram vs sparse memory footprint (<a href="">#14</a>)</li>
<li><a href=""><code>b61e5b0</code></a> Add GitHub repo link to h2histogram site TOC (<a href="">#13</a>)</li>
<li><a href=""><code>f8e23a6</code></a> Add u32 bucket counts as named sibling types (<a href="">#12</a>)</li>
<li><a href=""><code>37152c3</code></a> Add Notebook Kit site for h2histogram.org (alternative to <a href="">#10</a>) (<a href="">#11</a>)</li>
<li>See full diff in <a href="https://github.com/iopsystems/histogram/compare/v1.2.0...v1.3.1">compare view</a></li>
</ul>
</details>
<br />

Updates `niffler` from 3.0.0 to 3.0.1
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/luizirber/niffler/blob/main/CHANGELOG.md">niffler's changelog</a>.</em></p>
<blockquote>
<h2>[3.0.1] - 2026-04-29</h2>
<h3>Changed</h3>
<ul>
<li>Bump MSRV to 1.82.0 (<a href="">#73</a>)</li>
</ul>
<h3>Chore</h3>
<ul>
<li>Update version of bzip2 and liblzma (<a href="">#73</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ab86115</code></a> Update version of bzip2 and liblzma (<a href="">#73</a>)</li>
<li><a href=""><code>48255b0</code></a> Create dependabot.yml</li>
<li>See full diff in <a href="https://github.com/luizirber/niffler/compare/v3.0.0...v3.0.1">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 4.5.0 to 4.6.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v4.6.0</h2>
<h2>What's Changed</h2>
<p>This release adds first support for macOS walltime.</p>
<p>Please note that profiling and other instruments are not yet available on macOS and will come in a later update.</p>
<ul>
<li>Support macos walltime without profiling in codspeed-rust by <a href="https://github.com/GuillaumeLagrange"><code>@​GuillaumeLagrange</code></a> in <a href="">CodSpeedHQ/codspeed-rust#176</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.5.0...v4.6.0">https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.5.0...v4.6.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0c6ccae</code></a> Release 4.6.0</li>
<li><a href=""><code>fa2bd15</code></a> chore: bump use i32 for pid in instrument-hooks api</li>
<li><a href=""><code>8bbbe16</code></a> ci: add a macos integration test</li>
<li><a href=""><code>e24bedc</code></a> feat: add aarch64-apple-darwin artifacts to the release</li>
<li>See full diff in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.5.0...v4.6.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52fef6fc5dc8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.