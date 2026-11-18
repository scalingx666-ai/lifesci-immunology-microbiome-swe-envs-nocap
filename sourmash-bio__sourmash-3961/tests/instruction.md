# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [histogram](https://github.com/iopsystems/histogram) and [rand](https://github.com/rust-random/rand).

Updates `histogram` from 1.4.1 to 1.5.0
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/releases">histogram's releases</a>.</em></p>
<blockquote>
<h2>v1.5.0</h2>
<h2>What's Changed</h2>
<ul>
<li>QuantileResult: Add into_entries by <a href="https://github.com/Lorak-mmk"><code>@​Lorak-mmk</code></a> in <a href="">iopsystems/histogram#24</a></li>
<li>release: v1.5.0 by <a href="https://github.com/brayniac"><code>@​brayniac</code></a> in <a href="">iopsystems/histogram#25</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/Lorak-mmk"><code>@​Lorak-mmk</code></a> made their first contribution in <a href="">iopsystems/histogram#24</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/iopsystems/histogram/compare/v1.4.1...v1.5.0">https://github.com/iopsystems/histogram/compare/v1.4.1...v1.5.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/iopsystems/histogram/blob/main/CHANGELOG.md">histogram's changelog</a>.</em></p>
<blockquote>
<h2>[1.5.0] - 2026-07-01</h2>
<h3>Added</h3>
<ul>
<li><code>QuantilesResult::into_entries()</code> — consumes the result and returns the
quantile-to-bucket <code>BTreeMap</code> by value, allowing iterator transformations
without borrowing from the original result.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d0bb097</code></a> release: v1.5.0 (<a href="">#25</a>)</li>
<li><a href=""><code>143a9b1</code></a> QuantileResult: Add into_entries (<a href="">#24</a>)</li>
<li>See full diff in <a href="https://github.com/iopsystems/histogram/compare/v1.4.1...v1.5.0">compare view</a></li>
</ul>
</details>
<br />

Updates `rand` from 0.10.1 to 0.10.2
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-random/rand/blob/master/CHANGELOG.md">rand's changelog</a>.</em></p>
<blockquote>
<h2>[0.10.2] — 2026-07-02</h2>
<h3>Fixes</h3>
<ul>
<li>Fix possible memory safety violation due to deserialization of <code>UniformChar</code> from bad source (<a href="">#1790</a>)</li>
</ul>
<h3>Changes</h3>
<ul>
<li>Document required output order of fn <code>partial_shuffle</code> and apply <code>#[must_use]</code> (<a href="">#1769</a>)</li>
<li>Avoid usage of <code>unsafe</code> in contexts where non-local memory corruption could invalidate contract (<a href="">#1791</a>)</li>
</ul>
<p><a href="">#1769</a>: <a href="">rust-random/rand#1769</a>
<a href="">#1790</a>: <a href="">rust-random/rand#1790</a>
<a href="">#1791</a>: <a href="">rust-random/rand#1791</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1540ea3</code></a> Prepare rand 0.10.2 (<a href="">#1800</a>)</li>
<li><a href=""><code>a29964a</code></a> Bump chacha20 from 0.10.0 to 0.10.1 in the all-deps group (<a href="">#1801</a>)</li>
<li><a href=""><code>ced9491</code></a> Tweak docs for RngExt::random_range and SampleRange (<a href="">#1798</a>)</li>
<li><a href=""><code>db14664</code></a> Check UniformChar validity on deser (<a href="">#1790</a>)</li>
<li><a href=""><code>bea8620</code></a> Bump the all-deps group with 2 updates (<a href="">#1796</a>)</li>
<li><a href=""><code>4f44932</code></a> Bump actions/cache from 5 to 6 (<a href="">#1795</a>)</li>
<li><a href=""><code>b999a13</code></a> Bump actions/checkout from 6 to 7 (<a href="">#1794</a>)</li>
<li><a href=""><code>aeab810</code></a> Avoid unsafe where safety depends on non-local values (<a href="">#1791</a>)</li>
<li><a href=""><code>1896d7c</code></a> Add typos CI job (<a href="">#1789</a>)</li>
<li><a href=""><code>43eddee</code></a> Bump the all-deps group with 2 updates (<a href="">#1788</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/rust-random/rand/compare/0.10.1...0.10.2">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1536112db54a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.