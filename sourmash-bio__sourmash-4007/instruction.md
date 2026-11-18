# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [serde_json](https://github.com/serde-rs/json) and [proptest](https://github.com/proptest-rs/proptest).

Updates `serde_json` from 1.0.151 to 1.0.152
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.152</h2>
<ul>
<li>Preserve sign of <code>-0</code> in arbitrary_precision mode (<a href="">#1346</a>, thanks <a href="https://github.com/yuxi-liu-wired"><code>@​yuxi-liu-wired</code></a>)</li>
<li>Fix comparison of large non-integer values with f32::INFINITY (<a href="">#1347</a>, thanks <a href="https://github.com/yuxi-liu-wired"><code>@​yuxi-liu-wired</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c9f1e3b</code></a> Release 1.0.152</li>
<li><a href=""><code>854fc70</code></a> Touch up PR 1347</li>
<li><a href=""><code>80a5406</code></a> Merge pull request <a href="">#1347</a> from yuxi-liu-wired/pr/partialeq-f32</li>
<li><a href=""><code>76e44e2</code></a> Merge pull request 1346 from yuxi-liu-wired/pr/ap-negative-zero</li>
<li><a href=""><code>d8bbd39</code></a> Value == f32 is false for numbers outside the range of f32</li>
<li><a href=""><code>65a38ed</code></a> Keep the sign of -0 in Value with arbitrary_precision</li>
<li><a href=""><code>afdf6fc</code></a> Ignore clone_on_copy clippy lint in test</li>
<li><a href=""><code>577729e</code></a> Resolve deprecated f64 constants warning</li>
<li><a href=""><code>a3e9758</code></a> Merge pull request <a href="">#1334</a> from xtqqczze/authors</li>
<li><a href=""><code>99edc94</code></a> Remove deprecated package authors field from Cargo.toml</li>
<li>See full diff in <a href="https://github.com/serde-rs/json/compare/v1.0.151...v1.0.152">compare view</a></li>
</ul>
</details>
<br />

Updates `proptest` from 1.11.0 to 1.12.0
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>70cf37d</code></a> Merge pull request <a href="">#675</a> from proptest-rs/prep-1.12</li>
<li><a href=""><code>729e0ff</code></a> prepare next releases and fix panic handling</li>
<li><a href=""><code>28c1fad</code></a> Merge pull request <a href="">#664</a> from Expyron/main</li>
<li><a href=""><code>5ddd9a4</code></a> Merge pull request <a href="">#668</a> from toddATavail/fix-fork-persisted-failure</li>
<li><a href=""><code>a6a9ac7</code></a> Merge pull request <a href="">#673</a> from glaziermag/fix-book-deploy</li>
<li><a href=""><code>d57d88b</code></a> Replace <code>rand_chacha</code> with <code>chacha20</code></li>
<li><a href=""><code>9411213</code></a> Deploy the book on pushes to main</li>
<li><a href=""><code>1719745</code></a> fix: terminate the fork replay when a persisted failure fails</li>
<li><a href=""><code>0f55b7a</code></a> test: a persisted failure in a forked test must be reported</li>
<li><a href=""><code>4b0594e</code></a> Merge pull request <a href="">#669</a> from proptest-rs/no-fail-fast</li>
<li>Additional commits viewable in <a href="https://github.com/proptest-rs/proptest/compare/v1.11.0...v1.12.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48b7f05d10b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.