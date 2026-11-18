# Issue

**Title:** Build(deps-rs): Bump bytes from 1.5.0 to 1.11.1

## Description

Bumps [bytes](https://github.com/tokio-rs/bytes) from 1.5.0 to 1.11.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/tokio-rs/bytes/releases">bytes's releases</a>.</em></p>
<blockquote>
<h2>Bytes v1.11.1</h2>
<h1>1.11.1 (February 3rd, 2026)</h1>
<ul>
<li>Fix integer overflow in <code>BytesMut::reserve</code></li>
</ul>
<h2>Bytes v1.11.0</h2>
<h1>1.11.0 (November 14th, 2025)</h1>
<ul>
<li>Bump MSRV to 1.57 (<a href="">#788</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>fix: <code>BytesMut</code> only reuse if src has remaining (<a href="">#803</a>)</li>
<li>Specialize <code>BytesMut::put::&lt;Bytes&gt;</code> (<a href="">#793</a>)</li>
<li>Reserve capacity in <code>BytesMut::put</code> (<a href="">#794</a>)</li>
<li>Change <code>BytesMut::remaining_mut</code> to use <code>isize::MAX</code> instead of <code>usize::MAX</code> (<a href="">#795</a>)</li>
</ul>
<h3>Internal changes</h3>
<ul>
<li>Guarantee address in <code>slice()</code> for empty slices. (<a href="">#780</a>)</li>
<li>Rename <code>Vtable::to_*</code> -&gt; <code>Vtable::into_*</code> (<a href="">#776</a>)</li>
<li>Fix latest clippy warnings (<a href="">#787</a>)</li>
<li>Ignore <code>BytesMut::freeze</code> doctest on wasm (<a href="">#790</a>)</li>
<li>Move <code>drop_fn</code> of <code>from_owner</code> into vtable (<a href="">#801</a>)</li>
</ul>
<h2>Bytes v1.10.1</h2>
<h1>1.10.1 (March 5th, 2025)</h1>
<h3>Fixed</h3>
<ul>
<li>Fix memory leak when using <code>to_vec</code> with <code>Bytes::from_owner</code> (<a href="">#773</a>)</li>
</ul>
<p><a href="">#773</a>: <a href="">tokio-rs/bytes#773</a></p>
<h2>Bytes v1.10.0</h2>
<h1>1.10.0 (February 3rd, 2025)</h1>
<h3>Added</h3>
<ul>
<li>Add feature to support platforms without atomic CAS (<a href="">#467</a>)</li>
<li><code>try_get_*</code> methods for <code>Buf</code> trait (<a href="">#753</a>)</li>
<li>Implement <code>Buf::chunks_vectored</code> for <code>Take</code> (<a href="">#617</a>)</li>
<li>Implement <code>Buf::chunks_vectored</code> for <code>VecDeque&lt;u8&gt;</code> (<a href="">#708</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Remove incorrect guarantee for <code>chunks_vectored</code> (<a href="">#754</a>)</li>
<li>Ensure that tests pass under <code>panic=abort</code> (<a href="">#749</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/tokio-rs/bytes/blob/master/CHANGELOG.md">bytes's changelog</a>.</em></p>
<blockquote>
<h1>1.11.1 (February 3rd, 2026)</h1>
<ul>
<li>Fix integer overflow in <code>BytesMut::reserve</code></li>
</ul>
<h1>1.11.0 (November 14th, 2025)</h1>
<ul>
<li>Bump MSRV to 1.57 (<a href="">#788</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>fix: <code>BytesMut</code> only reuse if src has remaining (<a href="">#803</a>)</li>
<li>Specialize <code>BytesMut::put::&lt;Bytes&gt;</code> (<a href="">#793</a>)</li>
<li>Reserve capacity in <code>BytesMut::put</code> (<a href="">#794</a>)</li>
<li>Change <code>BytesMut::remaining_mut</code> to use <code>isize::MAX</code> instead of <code>usize::MAX</code> (<a href="">#795</a>)</li>
</ul>
<h3>Internal changes</h3>
<ul>
<li>Guarantee address in <code>slice()</code> for empty slices. (<a href="">#780</a>)</li>
<li>Rename <code>Vtable::to_*</code> -&gt; <code>Vtable::into_*</code> (<a href="">#776</a>)</li>
<li>Fix latest clippy warnings (<a href="">#787</a>)</li>
<li>Ignore <code>BytesMut::freeze</code> doctest on wasm (<a href="">#790</a>)</li>
<li>Move <code>drop_fn</code> of <code>from_owner</code> into vtable (<a href="">#801</a>)</li>
</ul>
<h1>1.10.1 (March 5th, 2025)</h1>
<h3>Fixed</h3>
<ul>
<li>Fix memory leak when using <code>to_vec</code> with <code>Bytes::from_owner</code> (<a href="">#773</a>)</li>
</ul>
<h1>1.10.0 (February 3rd, 2025)</h1>
<h3>Added</h3>
<ul>
<li>Add feature to support platforms without atomic CAS (<a href="">#467</a>)</li>
<li><code>try_get_*</code> methods for <code>Buf</code> trait (<a href="">#753</a>)</li>
<li>Implement <code>Buf::chunks_vectored</code> for <code>Take</code> (<a href="">#617</a>)</li>
<li>Implement <code>Buf::chunks_vectored</code> for <code>VecDeque&lt;u8&gt;</code> (<a href="">#708</a>)</li>
</ul>
<h3>Fixed</h3>
<ul>
<li>Remove incorrect guarantee for <code>chunks_vectored</code> (<a href="">#754</a>)</li>
<li>Ensure that tests pass under <code>panic=abort</code> (<a href="">#749</a>)</li>
</ul>
<h1>1.9.0 (November 27, 2024)</h1>
<h3>Added</h3>
<ul>
<li>Add <code>Bytes::from_owner</code> to enable externally-allocated memory (<a href="">#742</a>)</li>
</ul>
<h3>Documented</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>417dccd</code></a> Release bytes v1.11.1 (<a href="">#820</a>)</li>
<li><a href=""><code>d0293b0</code></a> Merge commit from fork</li>
<li><a href=""><code>a7952fb</code></a> chore: prepare bytes v1.11.0 (<a href="">#804</a>)</li>
<li><a href=""><code>60cbb77</code></a> fix: <code>BytesMut</code> only reuse if src has remaining (<a href="">#803</a>)</li>
<li><a href=""><code>7ce330f</code></a> Move drop_fn of from_owner into vtable (<a href="">#801</a>)</li>
<li><a href=""><code>4b53a29</code></a> Tweak BytesMut::remaining_mut (<a href="">#795</a>)</li>
<li><a href=""><code>016fdbd</code></a> Reserve capacity in BytesMut::put (<a href="">#794</a>)</li>
<li><a href=""><code>ef7f257</code></a> Specialize BytesMut::put::&lt;Bytes&gt; (<a href="">#793</a>)</li>
<li><a href=""><code>8b4f54d</code></a> Ignore BytesMut::freeze doctest on wasm (<a href="">#790</a>)</li>
<li><a href=""><code>16132ad</code></a> Fix latest clippy warnings (<a href="">#787</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/tokio-rs/bytes/compare/v1.5.0...v1.11.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=bytes&package-manager=cargo&previous-version=1.5.0&new-version=1.11.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/sourmash-bio/sourmash/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bff8250affd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.