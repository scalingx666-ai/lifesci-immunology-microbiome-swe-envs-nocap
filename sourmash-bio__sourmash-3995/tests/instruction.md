# Issue

**Title:** Build(deps-rs): Bump the dependencies group across 1 directory with 9 updates

## Description

Bumps the dependencies group with 9 updates in the / directory:

| Package | From | To |
| --- | --- | --- |
| [camino](https://github.com/camino-rs/camino) | `1.2.4` | `1.2.6` |
| [cfg-if](https://github.com/rust-lang/cfg-if) | `1.0.4` | `1.0.5` |
| [histogram](https://github.com/iopsystems/histogram) | `1.5.0` | `1.6.0` |
| [log](https://github.com/rust-lang/log) | `0.4.33` | `0.4.34` |
| [serde](https://github.com/serde-rs/serde) | `1.0.228` | `1.0.229` |
| [serde_json](https://github.com/serde-rs/json) | `1.0.150` | `1.0.151` |
| [thiserror](https://github.com/dtolnay/thiserror) | `2.0.18` | `2.0.21` |
| [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust) | `5.0.1` | `5.0.2` |
| [rand](https://github.com/rust-random/rand) | `0.10.2` | `0.10.3` |

Updates `camino` from 1.2.4 to 1.2.6
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/releases">camino's releases</a>.</em></p>
<blockquote>
<h2>camino 1.2.6</h2>
<h3>Fixed</h3>
<ul>
<li>The <code>Utf8Path::ends_with</code> parameter is now called <code>child</code> to match <code>std::path::Path::ends_with</code>. Thanks <a href="https://github.com/hxperl">hxperl</a> for your first contribution!</li>
</ul>
<h2>camino 1.2.5</h2>
<h3>Fixed</h3>
<p>Removed unnecessary files from the package.</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/camino-rs/camino/blob/main/CHANGELOG.md">camino's changelog</a>.</em></p>
<blockquote>
<h2>[1.2.6] - 2026-09-15</h2>
<h3>Fixed</h3>
<ul>
<li>The <code>Utf8Path::ends_with</code> parameter is now called <code>child</code> to match <code>std::path::Path::ends_with</code>. Thanks <a href="https://github.com/hxperl">hxperl</a> for your first contribution!</li>
</ul>
<h2>[1.2.5] - 2026-07-28</h2>
<h3>Fixed</h3>
<p>Removed unnecessary files from the package.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>86ed283</code></a> [camino] version 1.2.6</li>
<li><a href=""><code>2a6345b</code></a> [meta] prepare changelog</li>
<li><a href=""><code>180581f</code></a> Name the ends_with parameter child, matching std's Path (<a href="">#131</a>)</li>
<li><a href=""><code>8cb6393</code></a> switch gh-pages deploy to newer style</li>
<li><a href=""><code>0b8668c</code></a> [camino] version 1.2.5</li>
<li><a href=""><code>2437e78</code></a> [meta] prepare changelog</li>
<li><a href=""><code>928c686</code></a> switch to an include list in the package (<a href="">#129</a>)</li>
<li><a href=""><code>089546b</code></a> remove claude detritus (<a href="">#128</a>)</li>
<li><a href=""><code>3a9bd8c</code></a> add back the link for From&lt;Box<!-- raw HTML omitted -->&gt; for Box&lt;Path&gt; (<a href="">#126</a>)</li>
<li>See full diff in <a href="https://github.com/camino-rs/camino/compare/camino-1.2.4...camino-1.2.6">compare view</a></li>
</ul>
</details>
<br />

Updates `cfg-if` from 1.0.4 to 1.0.5
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/releases">cfg-if's releases</a>.</em></p>
<blockquote>
<h2>v1.0.5</h2>
<ul>
<li>Add a note that this crate is deprecated, suggesting <code>cfg_select!</code> instead</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/blob/main/CHANGELOG.md">cfg-if's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/rust-lang/cfg-if/compare/v1.0.4...v1.0.5">1.0.5</a> - 2026-09-16</h2>
<ul>
<li>Add a note that this crate is deprecated, suggesting <code>cfg_select!</code> instead</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8b0a2b0</code></a> Deprecation notice + crate version bump</li>
<li><a href=""><code>efabe3f</code></a> Add a changelog entry for the upcoming deprecation notice</li>
<li><a href=""><code>a66c2d4</code></a> Bump actions/checkout from 6 to 7</li>
<li><a href=""><code>bda9677</code></a> Bump actions/checkout from 5 to 6</li>
<li>See full diff in <a href="https://github.com/rust-lang/cfg-if/compare/v1.0.4...v1.0.5">compare view</a></li>
</ul>
</details>
<br />

Updates `histogram` from 1.5.0 to 1.6.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/releases">histogram's releases</a>.</em></p>
<blockquote>
<h2>v1.6.0</h2>
<h2>What's Changed</h2>
<ul>
<li>chore: bump to 1.5.1-alpha.0 for next development iteration by <a href="https://github.com/brayniac"><code>@​brayniac</code></a> in <a href="">iopsystems/histogram#26</a></li>
<li>docs: correct grouping power for 0.1% error example by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#28</a></li>
<li>Add allocation-free cumulative quantile queries by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#29</a></li>
<li>Add opt-in compaction for retained histogram snapshots by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#30</a></li>
<li>Add checked merge and downsample for cumulative snapshots by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#31</a></li>
<li>Speed up dense histogram quantile reports by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#32</a></li>
<li>Add reset convenience API for dense histograms by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#33</a></li>
<li>Add allocation-free dense reporting and reusable snapshots by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#34</a></li>
<li>Vectorize checked dense u32 merge validation by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#35</a></li>
<li>Validate histogram invariants during deserialization by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#38</a></li>
<li>Add fused checked aggregation for owned dense histograms by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#39</a></li>
<li>release: v1.6.0 by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#40</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/iopsystems/histogram/compare/v1.5.0...v1.6.0">https://github.com/iopsystems/histogram/compare/v1.5.0...v1.6.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/blob/main/CHANGELOG.md">histogram's changelog</a>.</em></p>
<blockquote>
<h2>[1.6.0] - 2026-09-15</h2>
<h3>Added</h3>
<ul>
<li><code>checked_sum()</code> on <code>Histogram</code> and <code>Histogram32</code> aggregates a batch of
completed windows or per-writer histograms into one fresh owned result. Every
configuration is validated before allocation; addition and per-bucket overflow
detection are fused into one pass per source, and a failing private result is
discarded. On x86 an AVX2 specialization is selected at runtime after the
CPU feature check; other hosts use the portable path.</li>
<li><code>checked_add_assign()</code> on <code>Histogram</code> and <code>Histogram32</code>: allocation-free
in-place merge with two-pass overflow validation and no partial mutation on
failure. The <code>u32</code> validation pass reduces per-bucket overflow flags so large
arrays can vectorize.</li>
<li><code>reset()</code> on <code>Histogram</code> and <code>Histogram32</code> clears every bucket in place while
preserving configuration and the existing allocation.</li>
<li><code>load_into()</code> and <code>drain_into()</code> on <code>AtomicHistogram</code> and <code>AtomicHistogram32</code>
fill an existing dense destination, rejecting incompatible configurations
before any mutation.</li>
<li>Allocation-free <code>quantile_bucket()</code> and <code>quantile_buckets_into()</code> on
<code>Histogram</code> and <code>Histogram32</code>. Batches preserve request order and duplicates,
validate before writing, and share one forward rank scan.</li>
<li>Checked addition and downsampling on owned and borrowed cumulative snapshots,
for both counter widths. Transforms return owned output, validate input storage,
and recompute midpoint means; addition checks combined total-count overflow.</li>
<li>Opt-in <code>shrink_to_fit()</code> on owned sparse and cumulative histograms, with both
<code>u64</code> and <code>u32</code> counters, to reduce spare vector capacity before retention.</li>
<li>Allocation-free <code>quantile_bucket()</code> and <code>quantile_buckets_into()</code> queries on
owned and borrowed cumulative histograms, for both <code>u64</code> and <code>u32</code> counters.
Batch queries preserve request order and duplicates using caller-provided storage.</li>
<li><code>Error::InsufficientOutputCapacity</code> reports the required and available output
slots when a caller-provided query buffer is too short.</li>
</ul>
<h3>Changed</h3>
<ul>
<li>Dense quantile reports find the occupied bounds first, sum only that range,
and skip eight-counter blocks below each requested rank. Report metadata,
<code>u128</code> totals, validation and rank semantics are unchanged.</li>
<li>Deserialization validates <code>Config</code> and rebuilds dense, sparse and cumulative
histograms through their validating constructors; cumulative means are
recomputed from validated counts. Serialized field names and legacy JSON and
bincode round trips are preserved.</li>
<li><code>Config</code> construction rejects bucket geometries whose index or count fields
cannot fit <code>u32</code> before arithmetic can overflow.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e426290</code></a> release: v1.6.0 (<a href="">#40</a>)</li>
<li><a href=""><code>deedf16</code></a> Add fused checked aggregation for owned dense histograms (<a href="">#39</a>)</li>
<li><a href=""><code>4df6eb1</code></a> Validate histogram invariants during deserialization (<a href="">#38</a>)</li>
<li><a href=""><code>2562b8e</code></a> Vectorize checked dense u32 merge validation (<a href="">#35</a>)</li>
<li><a href=""><code>cb06339</code></a> Add allocation-free dense reporting and reusable snapshot APIs (<a href="">#34</a>)</li>
<li><a href=""><code>7b5343f</code></a> Add allocation-preserving reset for dense histograms (<a href="">#33</a>)</li>
<li><a href=""><code>af09231</code></a> Speed up dense histogram reports with bounded block scans (<a href="">#32</a>)</li>
<li><a href=""><code>2b4a80c</code></a> Add checked merge and downsample for cumulative snapshots (<a href="">#31</a>)</li>
<li><a href=""><code>787ffdd</code></a> Add opt-in compaction for retained snapshots (<a href="">#30</a>)</li>
<li><a href=""><code>5683cd1</code></a> Add allocation-free cumulative quantile queries (<a href="">#29</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/iopsystems/histogram/compare/v1.5.0...v1.6.0">compare view</a></li>
</ul>
</details>
<br />

Updates `log` from 0.4.33 to 0.4.34
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/log/releases">log's releases</a>.</em></p>
<blockquote>
<h2>0.4.34</h2>
<h2>What's Changed</h2>
<ul>
<li>doc: Add context-logger utility to README by <a href="https://github.com/alekseysidorov"><code>@​alekseysidorov</code></a> in <a href="">rust-lang/log#735</a></li>
<li>Add alloc support for boxed loggers by <a href="https://github.com/malezjaa"><code>@​malezjaa</code></a> in <a href="">rust-lang/log#737</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/alekseysidorov"><code>@​alekseysidorov</code></a> made their first contribution in <a href="">rust-lang/log#735</a></li>
<li><a href="https://github.com/malezjaa"><code>@​malezjaa</code></a> made their first contribution in <a href="">rust-lang/log#737</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.33...0.4.34">https://github.com/rust-lang/log/compare/0.4.33...0.4.34</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/log/blob/master/CHANGELOG.md">log's changelog</a>.</em></p>
<blockquote>
<h2>[0.4.34] - 2026-08-22</h2>
<h2>What's Changed</h2>
<ul>
<li>doc: Add context-logger utility to README by <a href="https://github.com/alekseysidorov"><code>@​alekseysidorov</code></a> in <a href="">rust-lang/log#735</a></li>
<li>Add alloc support for boxed loggers by <a href="https://github.com/malezjaa"><code>@​malezjaa</code></a> in <a href="">rust-lang/log#737</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/alekseysidorov"><code>@​alekseysidorov</code></a> made their first contribution in <a href="">rust-lang/log#735</a></li>
<li><a href="https://github.com/malezjaa"><code>@​malezjaa</code></a> made their first contribution in <a href="">rust-lang/log#737</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.33...0.4.34">https://github.com/rust-lang/log/compare/0.4.33...0.4.34</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8034743</code></a> Merge pull request <a href="">#738</a> from rust-lang/cargo/0.4.34</li>
<li><a href=""><code>7d1e24e</code></a> prepare for 0.4.34 release</li>
<li><a href=""><code>3b939b6</code></a> Merge pull request <a href="">#737</a> from malezjaa/master</li>
<li><a href=""><code>b88266c</code></a> Add alloc support for boxed loggers</li>
<li><a href=""><code>037d7a5</code></a> doc: Add context-logger utility to README</li>
<li>See full diff in <a href="https://github.com/rust-lang/log/compare/0.4.33...0.4.34">compare view</a></li>
</ul>
</details>
<br />

Updates `serde` from 1.0.228 to 1.0.229
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/serde/releases">serde's releases</a>.</em></p>
<blockquote>
<h2>v1.0.229</h2>
<ul>
<li>Update to syn 3</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7fc3b4c</code></a> Release 1.0.229</li>
<li><a href=""><code>6d6e9a1</code></a> Merge pull request <a href="">#3085</a> from dtolnay/syn3</li>
<li><a href=""><code>6dec3b7</code></a> Update to syn 3</li>
<li><a href=""><code>cfe6692</code></a> Resolve mut_mut pedantic clippy lint</li>
<li><a href=""><code>1023d07</code></a> Update actions/upload-artifact@v6 -&gt; v7</li>
<li><a href=""><code>dd682c2</code></a> Update actions/checkout@v6 -&gt; v7</li>
<li><a href=""><code>5f0f18b</code></a> Update ui test suite to nightly-2026-06-01</li>
<li><a href=""><code>63a1498</code></a> Regenerate stderr with trybuild normalization fixes</li>
<li><a href=""><code>fa7da4a</code></a> Fix unused_features warning</li>
<li><a href=""><code>6b1a178</code></a> Unpin CI miri toolchain</li>
<li>Additional commits viewable in <a href="https://github.com/serde-rs/serde/compare/v1.0.228...v1.0.229">compare view</a></li>
</ul>
</details>
<br />

Updates `serde_json` from 1.0.150 to 1.0.151
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.151</h2>
<ul>
<li>Add RawValue::from_string_unchecked (<a href="">#1331</a>, thanks <a href="https://github.com/WonderLawrence"><code>@​WonderLawrence</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>de85007</code></a> Release 1.0.151</li>
<li><a href=""><code>3b2b3c5</code></a> Merge pull request <a href="">#1331</a> from WonderLawrence/rawvalue-from-string-unchecked</li>
<li><a href=""><code>0406d96</code></a> Debug-assert well-formedness and no-whitespace in from_string_unchecked</li>
<li><a href=""><code>cf16f75</code></a> Add RawValue::from_string_unchecked</li>
<li><a href=""><code>827a315</code></a> Update actions/upload-artifact@v6 -&gt; v7</li>
<li><a href=""><code>cea36a5</code></a> Update actions/checkout@v6 -&gt; v7</li>
<li>See full diff in <a href="https://github.com/serde-rs/json/compare/v1.0.150...v1.0.151">compare view</a></li>
</ul>
</details>
<br />

Updates `thiserror` from 2.0.18 to 2.0.21
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/dtolnay/thiserror/releases">thiserror's releases</a>.</em></p>
<blockquote>
<h2>2.0.21</h2>
<ul>
<li>Fix parsing of generic unit variants in display expressions (<a href="">#459</a>)</li>
</ul>
<h2>2.0.20</h2>
<ul>
<li>Suppress redundant_field_names clippy lint in generated code (<a href="">#454</a>)</li>
</ul>
<h2>2.0.19</h2>
<ul>
<li>Update to syn 3</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b1827ee</code></a> Release 2.0.21</li>
<li><a href=""><code>58037b5</code></a> Merge pull request <a href="">#459</a> from dtolnay/turbofish</li>
<li><a href=""><code>f82a0cf</code></a> Keep track of nested turbofish depth</li>
<li><a href=""><code>72ea492</code></a> Raise required compiler to Rust 1.77</li>
<li><a href=""><code>72eea0d</code></a> Resolve io_other_error clippy lint in tests</li>
<li><a href=""><code>07f09a2</code></a> Raise required compiler to Rust 1.74</li>
<li><a href=""><code>2715388</code></a> Update ui test suite to nightly-2026-09-22</li>
<li><a href=""><code>5a306c7</code></a> Update ui test suite to nightly-2026-09-05</li>
<li><a href=""><code>ef9383b</code></a> Update ui test suite to nightly-2026-08-22</li>
<li><a href=""><code>8336b84</code></a> Update ui tests for version 2.0.20</li>
<li>Additional commits viewable in <a href="https://github.com/dtolnay/thiserror/compare/2.0.18...2.0.21">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 5.0.1 to 5.0.2
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v5.0.2</h2>
<h2>What's Changed</h2>
<ul>
<li>fix(divan): support threaded walltime benchmarks by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#189</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.1...v5.0.2">https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.1...v5.0.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>832f252</code></a> Release 5.0.2</li>
<li><a href=""><code>96e1aca</code></a> fix(divan): support threaded walltime benchmarks</li>
<li><a href=""><code>6666998</code></a> chore(deps): bump instrument-hooks to thread-safe C API</li>
<li><a href=""><code>cbde9bb</code></a> test(divan): add native threaded benchmark fixture</li>
<li>See full diff in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.1...v5.0.2">compare view</a></li>
</ul>
</details>
<br />

Updates `rand` from 0.10.2 to 0.10.3
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-random/rand/blob/master/CHANGELOG.md">rand's changelog</a>.</em></p>
<blockquote>
<h2>[0.10.3] — 2026-09-20</h2>
<h3>Fixes</h3>
<ul>
<li>Fix <code>WeightedIndex</code> panic when the sum of float weights is infinite; return <code>Error::Overflow</code> instead (<a href="">#1808</a>)</li>
<li>Fix spurious <code>Error::NonFinite</code> from <code>Uniform::new_inclusive</code> on large finite float ranges such as <code>0.0..=f64::MAX</code> (<a href="">#1821</a>)</li>
<li>Fix possible panic due to sampling a deserialized <code>Uniform&lt;char&gt;</code> (<a href="">#1831</a>)</li>
</ul>
<h3>Changes</h3>
<ul>
<li>Report exact remaining lengths from <code>WeightedIndex::weights()</code> and reduce overhead when reading weights (<a href="">#1838</a>)</li>
</ul>
<p><a href="">#1808</a>: <a href="">rust-random/rand#1808</a>
<a href="">#1821</a>: <a href="">rust-random/rand#1821</a>
<a href="">#1831</a>: <a href="">rust-random/rand#1831</a>
<a href="">#1838</a>: <a href="">rust-random/rand#1838</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9e7d328</code></a> Prepare rand 0.10.3 (<a href="">#1840</a>)</li>
<li><a href=""><code>f73ce74</code></a> Optimize WeightedIndex weight lookup and iteration (<a href="">#1838</a>)</li>
<li><a href=""><code>ef9e044</code></a> Avoid panic from deserialized <code>Uniform\&lt;char&gt;</code> where <code>range == 0</code> (<a href="">#1831</a>)</li>
<li><a href=""><code>c994eb1</code></a> docs: fix angle unit in quick start example (<a href="">#1839</a>)</li>
<li><a href=""><code>33dea4f</code></a> Test that WeightedIndex rejects INFINITY with Error::Overflow (<a href="">#1822</a>)</li>
<li><a href=""><code>94c9078</code></a> Fix Uniform::new_inclusive overflow on large finite float ranges (<a href="">#1821</a>)</li>
<li><a href=""><code>bb1262f</code></a> Use Xoshiro256PlusPlus in examples/rayon-monte-carlo.rs (<a href="">#1805</a>)</li>
<li><a href=""><code>521fab6</code></a> Stop pinning dependencies (<a href="">#1820</a>)</li>
<li><a href=""><code>3f7c433</code></a> Stop pinning dependencies</li>
<li><a href=""><code>cf4f73e</code></a> sample_efraimidis_spirakis: error on more than amount non-finite weights (<a href="">#1814</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/rust-random/rand/compare/0.10.2...0.10.3">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d603dbc2d64c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.