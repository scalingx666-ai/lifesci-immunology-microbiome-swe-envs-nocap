# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [serde_json](https://github.com/serde-rs/json) and [codspeed-criterion-compat](https://github.com/CodSpeedHQ/codspeed-rust).

Updates `serde_json` from 1.0.152 to 1.0.154
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.154</h2>
<ul>
<li>Support preserve_order in no_std builds (<a href="">#1333</a>, thanks <a href="https://github.com/razmser"><code>@​razmser</code></a>)</li>
</ul>
<h2>v1.0.153</h2>
<ul>
<li>Report invalid UTF-8 at the first bad byte (<a href="">#1345</a>, thanks <a href="https://github.com/00200200"><code>@​00200200</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>20572a6</code></a> Release 1.0.154</li>
<li><a href=""><code>a91bfaf</code></a> Fix RandomState links in map documentation</li>
<li><a href=""><code>3c932c0</code></a> Merge pull request <a href="">#1333</a> from razmser/no-std-preserve-order</li>
<li><a href=""><code>4b2d726</code></a> Release 1.0.153</li>
<li><a href=""><code>83335ee</code></a> Touch up PR 1345</li>
<li><a href=""><code>4b4810a</code></a> Resolve range_plus_one pedantic clippy lint</li>
<li><a href=""><code>8af71cc</code></a> Merge pull request <a href="">#1345</a> from 00200200/fix-invalid-utf8-error-column</li>
<li><a href=""><code>452afa2</code></a> Correct multiline raw UTF-8 error positions and simplify indexing</li>
<li><a href=""><code>e759c5b</code></a> Report invalid UTF-8 at the first bad byte.</li>
<li><a href=""><code>35ca8ef</code></a> Support preserve_order in no_std builds</li>
<li>See full diff in <a href="https://github.com/serde-rs/json/compare/v1.0.152...v1.0.154">compare view</a></li>
</ul>
</details>
<br />

Updates `codspeed-criterion-compat` from 5.0.2 to 5.0.3
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/CodSpeedHQ/codspeed-rust/releases">codspeed-criterion-compat's releases</a>.</em></p>
<blockquote>
<h2>v5.0.3</h2>
<h2>What's Changed</h2>
<ul>
<li>docs(cargo-codspeed): clarify BENCHNAME and --bench help by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#195</a></li>
<li>fix(criterion): send benchmark markers around iter_manual rounds by <a href="https://github.com/not-matthias"><code>@​not-matthias</code></a> in <a href="">CodSpeedHQ/codspeed-rust#195</a></li>
<li>ci: migrate to github default arm runners by <a href="https://github.com/lvaroqui"><code>@​lvaroqui</code></a> in <a href="">CodSpeedHQ/codspeed-rust#196</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/lvaroqui"><code>@​lvaroqui</code></a> made their first contribution in <a href="">CodSpeedHQ/codspeed-rust#196</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.2...v5.0.3">https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.2...v5.0.3</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5aaf570</code></a> Release 5.0.3</li>
<li><a href=""><code>add7af0</code></a> ci: migrate to github default arm runners (<a href="">#196</a>)</li>
<li><a href=""><code>d07bbd0</code></a> docs(cargo-codspeed): clarify BENCHNAME and --bench help (<a href="">#195</a>)</li>
<li>See full diff in <a href="https://github.com/CodSpeedHQ/codspeed-rust/compare/v5.0.2...v5.0.3">compare view</a></li>
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