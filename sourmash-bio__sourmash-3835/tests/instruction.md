# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [cfg-if](https://github.com/rust-lang/cfg-if) and [csv](https://github.com/BurntSushi/rust-csv).

Updates `cfg-if` from 1.0.3 to 1.0.4
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/releases">cfg-if's releases</a>.</em></p>
<blockquote>
<h2>v1.0.4</h2>
<ul>
<li>Support <code>cfg(true)</code> and <code>cfg(false)</code> (<a href="">#99</a>)</li>
<li>Set and test a MSRV of 1.32</li>
<li>Have a single top-level rule</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/blob/main/CHANGELOG.md">cfg-if's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/rust-lang/cfg-if/compare/v1.0.3...v1.0.4">1.0.4</a> - 2025-10-15</h2>
<ul>
<li>Support <code>cfg(true)</code> and <code>cfg(false)</code> (<a href="">#99</a>)</li>
<li>Set and test a MSRV of 1.32</li>
<li>Have a single top-level rule</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3510ca6</code></a> chore: release v1.0.4 (<a href="">#95</a>)</li>
<li><a href=""><code>15aec4a</code></a> Support <code>cfg(true)</code> and <code>cfg(false)</code> (<a href="">#99</a>)</li>
<li><a href=""><code>036c64e</code></a> Set and test a MSRV of 1.32</li>
<li><a href=""><code>5fd566f</code></a> Set <code>-Dwarnings</code> via CI env rather than <code>cfg</code></li>
<li><a href=""><code>8ef8e9f</code></a> Have a single top-level rule.</li>
<li><a href=""><code>2400b38</code></a> Document and test for a subtle case.</li>
<li>See full diff in <a href="https://github.com/rust-lang/cfg-if/compare/v1.0.3...v1.0.4">compare view</a></li>
</ul>
</details>
<br />

Updates `csv` from 1.3.1 to 1.4.0
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4a3997e</code></a> 1.4.0</li>
<li><a href=""><code>a0a3c9e</code></a> csv-core-0.1.13</li>
<li><a href=""><code>f8e6b07</code></a> deps: switch <code>serde</code> dependency to <code>serde_core</code></li>
<li><a href=""><code>7c7c135</code></a> style: address many Clippy lints</li>
<li><a href=""><code>5b2da18</code></a> doc: simplify tutorial section on accessing headers</li>
<li><a href=""><code>633552a</code></a> perf: serialize 128-bit integers via <code>itoa</code></li>
<li><a href=""><code>e9f06f4</code></a> lint: fix <code>needless_lifetimes</code> and <code>mismatched_lifetime_syntaxes</code></li>
<li><a href=""><code>9dab947</code></a> test: fix broken test after panic message change</li>
<li><a href=""><code>da00088</code></a> style: address many Clippy lints</li>
<li><a href=""><code>f973cd4</code></a> enum: use <code>#[non_exhaustive]</code> instead of <code>#[doc(hidden)]</code> variant</li>
<li>Additional commits viewable in <a href="https://github.com/BurntSushi/rust-csv/compare/1.3.1...1.4.0">compare view</a></li>
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
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd09b1131683`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.