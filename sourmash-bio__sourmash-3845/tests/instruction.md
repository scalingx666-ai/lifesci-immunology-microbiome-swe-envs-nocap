# Issue

**Title:** Build(deps-rs): Bump the dependencies group with 2 updates

## Description

Bumps the dependencies group with 2 updates: [memmap2](https://github.com/RazrFalcon/memmap2-rs) and [proptest](https://github.com/proptest-rs/proptest).

Updates `memmap2` from 0.9.8 to 0.9.9
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/RazrFalcon/memmap2-rs/blob/master/CHANGELOG.md">memmap2's changelog</a>.</em></p>
<blockquote>
<h2>[0.9.9] - 2025-10-21</h2>
<h3>Fixed</h3>
<ul>
<li>Fix compilation on visionOS (and other apple operating systems).
<a href="https://github.com/sinkingsugar"><code>@​sinkingsugar</code></a></li>
<li>Do not assume <code>isize::MAX</code> fits in a <code>u64</code>.
<a href="https://github.com/ThomasHabets"><code>@​ThomasHabets</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>cc94666</code></a> Merge pull request <a href="">#158</a> from RazrFalcon/release/v0.9.9</li>
<li><a href=""><code>bfb74b1</code></a> Update changelog and bump version to v0.9.9</li>
<li><a href=""><code>83bf8cf</code></a> Merge pull request <a href="">#155</a> from ThomasHabets/safe-128</li>
<li><a href=""><code>5f753ab</code></a> Update src/lib.rs</li>
<li><a href=""><code>7e839b9</code></a> Merge pull request <a href="">#157</a> from sinkingsugar/master</li>
<li><a href=""><code>1ab625b</code></a> Add visionOS CI check to ensure compilation</li>
<li><a href=""><code>d0cbc33</code></a> Replace individual Apple OS checks with target_vendor = &quot;apple&quot;</li>
<li><a href=""><code>5a30f6b</code></a> Add visionOS support</li>
<li><a href=""><code>4f3d1aa</code></a> Future proof <code>validate_len()</code> for 128bit</li>
<li>See full diff in <a href="https://github.com/RazrFalcon/memmap2-rs/compare/v0.9.8...v0.9.9">compare view</a></li>
</ul>
</details>
<br />

Updates `proptest` from 1.8.0 to 1.9.0
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b2d358b</code></a> prep 1.9.0 release (<a href="">#607</a>)</li>
<li><a href=""><code>67a1fe4</code></a> Merge pull request <a href="">#606</a> from proptest-rs/fix-test</li>
<li><a href=""><code>7190be9</code></a> fix doctest and cleanup warnings</li>
<li><a href=""><code>c1a49e6</code></a> Merge pull request <a href="">#589</a> from bschoenmaeckers/assume_ok</li>
<li><a href=""><code>411e580</code></a> Merge pull request <a href="">#546</a> from serprex/remove-lazy-static</li>
<li><a href=""><code>a54d0a9</code></a> Merge branch 'main' into remove-lazy-static</li>
<li><a href=""><code>4b78455</code></a> Merge pull request <a href="">#605</a> from proptest-rs/msrv-1.82</li>
<li><a href=""><code>0454e5d</code></a> bump msrv to 1.82</li>
<li><a href=""><code>b59a691</code></a> Merge remote-tracking branch 'origin/main' into assume_ok</li>
<li><a href=""><code>9b121ca</code></a> Review</li>
<li>Additional commits viewable in <a href="https://github.com/proptest-rs/proptest/compare/v1.8.0...v1.9.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b183c75c9e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.