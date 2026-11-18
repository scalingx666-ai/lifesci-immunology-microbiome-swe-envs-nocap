# Issue

**Title:** Build(deps-py): Update bitstring requirement from <5,>=3.1.9 to >=3.1.9,<6 in the dependencies group

## Description

Updates the requirements on [bitstring](https://github.com/scott-griffiths/bitstring) to permit the latest version.
Updates `bitstring` to 5.0.0
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/scott-griffiths/bitstring/blob/main/release_notes.md">bitstring's changelog</a>.</em></p>
<blockquote>
<h2>October 2026: version 5.0.0 released</h2>
<p>A major release which completes the move to using the <code>tibs</code> Rust library as the core.</p>
<p>Performance has been a major driver in this release, and benchmark suite
shows a geometric mean of around 4x faster than 4.4. The largest
gains are in bulk work on <code>Array</code> objects, searching, packing and unpacking
multi-token formats, and sequential reading.</p>
<table>
<thead>
<tr>
<th>benchmark</th>
<th align="right">speedup</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>array_ops</code></td>
<td align="right">73.8x</td>
</tr>
<tr>
<td><code>findall_patterns</code></td>
<td align="right">36.2x</td>
</tr>
<tr>
<td><code>pack_unpack</code></td>
<td align="right">19.8x</td>
</tr>
<tr>
<td><code>read_mixed</code></td>
<td align="right">9.9x</td>
</tr>
<tr>
<td><code>sequential_read</code></td>
<td align="right">6.3x</td>
</tr>
<tr>
<td><code>array_indexing</code></td>
<td align="right">4.7x</td>
</tr>
<tr>
<td><code>count_set_bits</code></td>
<td align="right">4.5x</td>
</tr>
<tr>
<td><code>edit_inplace</code></td>
<td align="right">3.2x</td>
</tr>
<tr>
<td><code>cut_and_compare</code></td>
<td align="right">2.9x</td>
</tr>
<tr>
<td><code>bitwise_large</code></td>
<td align="right">2.6x</td>
</tr>
<tr>
<td><code>build_from_tokens</code></td>
<td align="right">1.9x</td>
</tr>
<tr>
<td><code>array_ops_fallback</code></td>
<td align="right">1.6x</td>
</tr>
<tr>
<td><code>slicing</code></td>
<td align="right">1.5x</td>
</tr>
<tr>
<td><code>create_small</code></td>
<td align="right">1.5x</td>
</tr>
<tr>
<td><code>grow_and_splice</code></td>
<td align="right">1.4x</td>
</tr>
<tr>
<td><code>bitwise_or</code></td>
<td align="right">1.2x</td>
</tr>
<tr>
<td><code>prime_sieve</code></td>
<td align="right">1.2x</td>
</tr>
<tr>
<td><code>interpret_small</code></td>
<td align="right">1.1x</td>
</tr>
</tbody>
</table>
<p>There are some significant breaking changes, though most are easy to rewrite.
See <a href="https://bitstring.readthedocs.io/en/latest/upgrading_to_version_5.html">https://bitstring.readthedocs.io/en/latest/upgrading_to_version_5.html</a> for
more details. If you don't need the new features or speed then the simplest
route is to pin your bitstring dependency to &lt;5.0 and stay using 4.x.</p>
<h4>Bigger breaking changes</h4>
<ul>
<li>Dropped support for Python 3.8, 3.9 and 3.10. The minimum supported version
is now Python 3.11.</li>
<li>Removed the <code>ConstBitStream</code> and <code>BitStream</code> classes. Use <code>Reader(Bits(...))</code>
for sequential reading, or <code>Reader(BitArray(...))</code> if the data also needs to
be mutated.</li>
<li><code>find()</code> and <code>rfind()</code> now return <code>int | None</code> instead of <code>(pos,)</code> or <code>()</code>.
Test with <code>result is not None</code>, as bit position zero is a valid match.</li>
<li>Removed the <code>len</code> and <code>length</code> properties. Use <code>len(bits)</code> instead.</li>
<li>Removed integer construction and the length-only keyword form. Use
<code>Bits.from_zeros(100)</code> instead of <code>Bits(100)</code> or <code>BitArray(length=100)</code>.</li>
<li><code>Dtype.build()</code> and <code>Dtype.parse()</code> have been renamed to <code>Dtype.pack()</code> and
<code>Dtype.unpack()</code>.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4217a37</code></a> Some more small docs fixes.</li>
<li><a href=""><code>26096b8</code></a> Lots of small docs fixes.</li>
<li><a href=""><code>4340f2d</code></a> Preparing for 5.0.0 release.</li>
<li><a href=""><code>1aac9ea</code></a> Better LLM discoverability and links to tibs.</li>
<li><a href=""><code>105ce31</code></a> Updates possible now that Python 3.11 is the minimum.</li>
<li><a href=""><code>03d91f4</code></a> Lots of simplification refactors mainly to use tibs more when possible.</li>
<li><a href=""><code>d5ae650</code></a> Yet more minor fixes.</li>
<li><a href=""><code>db0c238</code></a> Yet more minor fixes.</li>
<li><a href=""><code>8e71100</code></a> Mostly docs fixes.</li>
<li><a href=""><code>6b54777</code></a> Breaking change to not allow literals like 110b, 0x0x550x5 etc.</li>
<li>Additional commits viewable in <a href="https://github.com/scott-griffiths/bitstring/compare/bitstring-3.1.9...5.0.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4cfdd7f088c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.