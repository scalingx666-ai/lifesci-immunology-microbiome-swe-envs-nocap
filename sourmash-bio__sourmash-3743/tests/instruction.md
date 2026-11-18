# Issue

**Title:** Build(deps): Bump rand from 0.9.1 to 0.9.2

## Description

Bumps [rand](https://github.com/rust-random/rand) from 0.9.1 to 0.9.2.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-random/rand/blob/master/CHANGELOG.md">rand's changelog</a>.</em></p>
<blockquote>
<h2>[0.9.2 — 2025-07-20]</h2>
<h3>Deprecated</h3>
<ul>
<li>Deprecate <code>rand::rngs::mock</code> module and <code>StepRng</code> generator (<a href="">#1634</a>)</li>
</ul>
<h3>Additions</h3>
<ul>
<li>Enable <code>WeightedIndex&lt;usize&gt;</code> (de)serialization (<a href="">#1646</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d3dd415</code></a> Prepare rand_core 0.9.2 (<a href="">#1605</a>)</li>
<li><a href=""><code>99fabd2</code></a> Prepare rand_core 0.9.2</li>
<li><a href=""><code>c7fe1c4</code></a> rand: re-export <code>rand_core</code> (<a href="">#1604</a>)</li>
<li><a href=""><code>db2b1e0</code></a> rand: re-export <code>rand_core</code></li>
<li><a href=""><code>ee1d96f</code></a> rand_core: implement reborrow for <code>UnwrapMut</code> (<a href="">#1595</a>)</li>
<li><a href=""><code>e0eb2ee</code></a> rand_core: implement reborrow for <code>UnwrapMut</code></li>
<li><a href=""><code>975f602</code></a> fixup clippy 1.85 warnings</li>
<li><a href=""><code>775b05b</code></a> Relax <code>Sized</code> requirements for blanket impls (<a href="">#1593</a>)</li>
<li>See full diff in <a href="https://github.com/rust-random/rand/compare/rand_core-0.9.1...rand_core-0.9.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=rand&package-manager=cargo&previous-version=0.9.1&new-version=0.9.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e204f6624736`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.