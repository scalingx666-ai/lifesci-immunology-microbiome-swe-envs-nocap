# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 5 updates

## Description

Bumps the dependencies group with 5 updates:

| Package | From | To |
| --- | --- | --- |
| [getset](https://github.com/jbaublitz/getset) | `0.1.6` | `0.1.7` |
| [histogram](https://github.com/iopsystems/histogram) | `1.3.1` | `1.4.1` |
| [log](https://github.com/rust-lang/log) | `0.4.29` | `0.4.32` |
| [serde_json](https://github.com/serde-rs/json) | `1.0.149` | `1.0.150` |
| [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust) | `4.6.0` | `4.7.0` |

Updates `getset` from 0.1.6 to 0.1.7
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/jbaublitz/getset/releases">getset's releases</a>.</em></p>
<blockquote>
<h2>v0.1.7</h2>
<p><a href="https://github.com/jbaublitz/getset/issues?q=is%3Aissue%20state%3Aclosed%20milestone%3Av0.1.7">https://github.com/jbaublitz/getset/issues?q=is%3Aissue%20state%3Aclosed%20milestone%3Av0.1.7</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e9204af</code></a> Merge pull request <a href="">#135</a> from jbaublitz/release-v0.1.7</li>
<li><a href=""><code>263f2c8</code></a> v0.1.7</li>
<li><a href=""><code>4d33db9</code></a> Merge pull request <a href="">#134</a> from jbaublitz/issue-getset-132</li>
<li><a href=""><code>3c801bd</code></a> Remove proc-macro-error2 as a dependency</li>
<li>See full diff in <a href="https://github.com/jbaublitz/getset/compare/v0.1.6...v0.1.7">compare view</a></li>
</ul>
</details>
<br />

Updates `histogram` from 1.3.1 to 1.4.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/releases">histogram's releases</a>.</em></p>
<blockquote>
<h2>v1.4.1</h2>
<h2>What's Changed</h2>
<ul>
<li>Add mean() to borrowed CumulativeRO Ref views by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#21</a></li>
<li>release: v1.4.1 by <a href="https://github.com/thinkingfish"><code>@​thinkingfish</code></a> in <a href="">iopsystems/histogram#22</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/iopsystems/histogram/compare/v1.4.0...v1.4.1">https://github.com/iopsystems/histogram/compare/v1.4.0...v1.4.1</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/blob/main/CHANGELOG.md">histogram's changelog</a>.</em></p>
<blockquote>
<h2>[1.4.1] - 2026-05-19</h2>
<h3>Added</h3>
<ul>
<li>Midpoint-based <code>mean()</code> on the borrowed <code>CumulativeROHistogramRef</code> /
<code>CumulativeROHistogram32Ref</code> views. The mean is stored on the view
(computed once at construction, or carried over from the owned
histogram's cached value), so <code>mean()</code> is a cheap field access exposed
just like <code>count()</code> — no per-call streaming computation — letting a
zero-alloc reducer fold it in directly. Returns <code>None</code> for an empty
histogram.</li>
</ul>
<h3>Changed</h3>
<ul>
<li><code>CumulativeROHistogramRef</code> / <code>CumulativeROHistogram32Ref</code> no longer
implement <code>Eq</code> (they now carry an <code>f64</code> mean); <code>PartialEq</code> is retained.</li>
</ul>
<h2>[1.4.0] - 2026-05-19</h2>
<h3>Added</h3>
<ul>
<li>Midpoint-based <code>mean()</code> on <code>CumulativeROHistogram</code> / <code>CumulativeROHistogram32</code>
— the mean of all observations, estimated from bucket midpoints, computed
once at construction time across <code>from_parts</code>, <code>From&lt;&amp;Histogram&gt;</code>, and
<code>From&lt;&amp;SparseHistogram&gt;</code>. Returns <code>None</code> for an empty histogram.</li>
</ul>
<h3>Changed</h3>
<ul>
<li><code>CumulativeROHistogram</code> / <code>CumulativeROHistogram32</code> no longer implement <code>Eq</code>
(they now store an <code>f64</code> mean); <code>PartialEq</code> is retained. The borrowed
<code>*Ref</code> view types are unaffected.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>07e228d</code></a> release: v1.4.1 (<a href="">#22</a>)</li>
<li><a href=""><code>5b08a9c</code></a> Add mean() to borrowed CumulativeRO Ref views (<a href="">#21</a>)</li>
<li><a href=""><code>f074613</code></a> release: v1.4.0 (<a href="">#20</a>)</li>
<li><a href=""><code>f4858d0</code></a> Add midpoint-based mean to CumulativeRO histogram (<a href="">#19</a>)</li>
<li>See full diff in <a href="https://github.com/iopsystems/histogram/compare/v1.3.1...v1.4.1">compare view</a></li>
</ul>
</details>
<br />

Updates `log` from 0.4.29 to 0.4.32
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/log/releases">log's releases</a>.</em></p>
<blockquote>
<h2>0.4.32</h2>
<h2>What's Changed</h2>
<ul>
<li>Support <code>Value</code> -&gt; string conversions with <code>kv</code> + <code>std</code> features instead of <code>kv_std</code> by <a href="https://github.com/tisonkun"><code>@​tisonkun</code></a> in <a href="">rust-lang/log#729</a></li>
<li>Prepare for 0.4.32 release by <a href="https://github.com/KodrAus"><code>@​KodrAus</code></a> in <a href="">rust-lang/log#730</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.31...0.4.32">https://github.com/rust-lang/log/compare/0.4.31...0.4.32</a></p>
<h2>0.4.31</h2>
<h2>What's Changed</h2>
<ul>
<li>fix typos in kv compile errors and log documentation by <a href="https://github.com/Isvane"><code>@​Isvane</code></a> in <a href="">rust-lang/log#726</a></li>
<li>Leverage static str key when possible by <a href="https://github.com/tisonkun"><code>@​tisonkun</code></a> in <a href="">rust-lang/log#727</a></li>
<li>Prepare for 0.4.31 release by <a href="https://github.com/KodrAus"><code>@​KodrAus</code></a> in <a href="">rust-lang/log#728</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/Isvane"><code>@​Isvane</code></a> made their first contribution in <a href="">rust-lang/log#726</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.30...0.4.31">https://github.com/rust-lang/log/compare/0.4.30...0.4.31</a></p>
<h2>0.4.30</h2>
<h3>What's Changed</h3>
<ul>
<li>Support capturing of <code>std::net</code> types by <a href="https://github.com/KodrAus"><code>@​KodrAus</code></a> in <a href="">rust-lang/log#724</a></li>
</ul>
<h3>New Contributors</h3>
<ul>
<li><a href="https://github.com/V0ldek"><code>@​V0ldek</code></a> made their first contribution in <a href="">rust-lang/log#720</a></li>
<li><a href="https://github.com/woodruffw"><code>@​woodruffw</code></a> made their first contribution in <a href="">rust-lang/log#723</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.29...0.4.30">https://github.com/rust-lang/log/compare/0.4.29...0.4.30</a></p>
<h3>Notable Changes</h3>
<ul>
<li>MSRV is bumped to 1.71.0 in <a href="">rust-lang/log#723</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/log/blob/master/CHANGELOG.md">log's changelog</a>.</em></p>
<blockquote>
<h2>[0.4.32] - 2026-06-04</h2>
<h3>What's Changed</h3>
<ul>
<li>Support <code>Value</code> -&gt; string conversions with <code>kv</code> + <code>std</code> features instead of <code>kv_std</code> by <a href="https://github.com/tisonkun"><code>@​tisonkun</code></a> in <a href="">rust-lang/log#729</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.31...0.4.32">https://github.com/rust-lang/log/compare/0.4.31...0.4.32</a></p>
<h2>[0.4.31] - 2026-06-02</h2>
<h3>What's Changed</h3>
<ul>
<li>Leverage static str key when possible by <a href="https://github.com/tisonkun"><code>@​tisonkun</code></a> in <a href="">rust-lang/log#727</a></li>
</ul>
<h3>New Contributors</h3>
<ul>
<li><a href="https://github.com/Isvane"><code>@​Isvane</code></a> made their first contribution in <a href="">rust-lang/log#726</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.30...0.4.31">https://github.com/rust-lang/log/compare/0.4.30...0.4.31</a></p>
<h2>[0.4.30] - 2026-05-21</h2>
<h3>What's Changed</h3>
<ul>
<li>Support capturing of <code>std::net</code> types by <a href="https://github.com/KodrAus"><code>@​KodrAus</code></a> in <a href="">rust-lang/log#724</a></li>
</ul>
<h3>New Contributors</h3>
<ul>
<li><a href="https://github.com/V0ldek"><code>@​V0ldek</code></a> made their first contribution in <a href="">rust-lang/log#720</a></li>
<li><a href="https://github.com/woodruffw"><code>@​woodruffw</code></a> made their first contribution in <a href="">rust-lang/log#723</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/rust-lang/log/compare/0.4.29...0.4.30">https://github.com/rust-lang/log/compare/0.4.29...0.4.30</a></p>
<h3>Notable Changes</h3>
<ul>
<li>MSRV is bumped to 1.71.0 in <a href="">rust-lang/log#723</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a5b5b21</code></a> Merge pull request <a href="">#730</a> from rust-lang/cargo/0.4.32</li>
<li><a href=""><code>c8d3b12</code></a> prepare for 0.4.32 release</li>
<li><a href=""><code>ce6cd9f</code></a> Merge pull request <a href="">#729</a> from tisonkun/kv-std-support</li>
<li><a href=""><code>20b3b05</code></a> drop cfg-feature=kv as it is already met</li>
<li><a href=""><code>7bc1200</code></a> kv::std_support may not need value-bag</li>
<li><a href=""><code>5808392</code></a> Merge pull request <a href="">#728</a> from rust-lang/cargo/0.4.31</li>
<li><a href=""><code>86d739f</code></a> prepare for 0.4.31 release</li>
<li><a href=""><code>c906cfb</code></a> Merge pull request <a href="">#727</a> from tisonkun/leverage-static-str-key-when-possible</li>
<li><a href=""><code>756c279</code></a> leverage str literal as well</li>
<li><a href=""><code>3dd250d</code></a> rename Key::from_static_str to from_str_static</li>
<li>Additional commits viewable in <a href="https://github.com/rust-lang/log/compare/0.4.29...0.4.32">compare view</a></li>
</ul>
</details>
<br />

Updates `serde_json` from 1.0.149 to 1.0.150
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.150</h2>
<ul>
<li>Reject non-string enum object keys (<a href="">#1324</a>, thanks <a href="https://github.com/puneetdixit200"><code>@​puneetdixit200</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a1ae73a</code></a> Release 1.0.150</li>
<li><a href=""><code>1a360b0</code></a> Merge pull request <a href="">#1324</a> from puneetdixit200/reject-non-string-enum-keys</li>
<li><a href=""><code>2037b63</code></a> Reject non-string enum object keys</li>
<li><a href=""><code>5d30df6</code></a> Resolve manual_assert_eq pedantic clippy lint</li>
<li><a href=""><code>dc8003a</code></a> Raise required compiler for preserve_order feature to 1.85</li>
<li><a href=""><code>a42fa98</code></a> Unpin CI miri toolchain</li>
<li><a href=""><code>684a60e</code></a> Pin CI miri to nightly-2026-02-11</li>
<li><a href=""><code>7c7da33</code></a> Raise required compiler to Rust 1.71</li>
<li><a href=""><code>acf4850</code></a> Simplify Number::is_f64</li>
<li><a href=""><code>6b8ceab</code></a> Resolve unnecessary_map_or clippy lint</li>
<li>Additional commits viewable in <a href="https://github.com/serde-rs/json/compare/v1.0.149...v1.0.150">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 4.6.0 to 4.7.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v4.7.0</h2>
<h2>What's Changed</h2>
<h3>Manual sampling for criterion</h3>
<blockquote>
<p><strong>Note:</strong> ignored under CodSpeed simulation mode (single measured iteration). Only takes effect in walltime mode.</p>
</blockquote>
<p>We introduced a new finer control way of defining a criterion benchmark to have full control over how many times your code is ran.<br />
This bypasses criterion's original sampler, which we still recommend using if you do not have specific control needs.</p>
<pre lang="rust"><code>use codspeed_criterion_compat::{criterion_group, criterion_main, Criterion, IterManualOptions};
<p>fn bench_my_function(c: &amp;mut Criterion) {<br />
c.bench_function(&quot;my_function&quot;, |b| {<br />
b.iter_manual_unstable(<br />
IterManualOptions::new()<br />
.rounds(5)   // 5 measurement samples, can be lower than criterion's imposed 10<br />
.iters(1000)  // 1000 calls per sample<br />
.warmup(5),   // 5 unmeasured warmup iterations<br />
|| my_function(),<br />
);<br />
});<br />
}</p>
<p>criterion_group!(benches, bench_my_function);<br />
criterion_main!(benches);<br />
</code></pre></p>
<p>Please note that this API is still under development and may change with future releases.</p>
<ul>
<li>fix(cargo-codspeed): forward args after <code>--</code> to bench binaries by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#179</a></li>
<li>chore: bump instrument-hooks by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#178</a></li>
<li>feat(criterion-compat): add <code>iter_manual</code> to have finer control over the iteration loop by <a href="https://github.com/GuillaumeLagrange"><code>@​GuillaumeLagrange</code></a> in <a href="">CodSpeedHQ/codspeed-rust#180</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.6.0...v4.7.0">https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.6.0...v4.7.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>99c7b5a</code></a> Release 4.7.0</li>
<li><a href=""><code>e8a25a8</code></a> chore: shard criterion benchmarks</li>
<li><a href=""><code>5f145be</code></a> fix: fix crash when all samples have the same value</li>
<li><a href=""><code>26cfa70</code></a> feat(criterion-compat): add <code>iter_manual</code> to have finer control over the iter...</li>
<li><a href=""><code>6c54971</code></a> chore: bump instrument-hooks</li>
<li><a href=""><code>6072a98</code></a> fix(cargo-codspeed): forward args after <code>--</code> to bench binaries</li>
<li>See full diff in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v4.6.0...v4.7.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fc4ef01023f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.