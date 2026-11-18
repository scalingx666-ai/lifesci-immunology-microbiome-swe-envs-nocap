# Issue

**Title:** Build(deps-rs): Bump rand from 0.10.0 to 0.10.1

## Description

Bumps [rand](https://github.com/rust-random/rand) from 0.10.0 to 0.10.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-random/rand/blob/master/CHANGELOG.md">rand's changelog</a>.</em></p>
<blockquote>
<h2>[0.10.1] — 2026-02-11</h2>
<p>This release includes a fix for a soundness bug; see <a href="">#1763</a>.</p>
<h3>Changes</h3>
<ul>
<li>Document panic behavior of <code>make_rng</code> and add <code>#[track_caller]</code> (<a href="">#1761</a>)</li>
<li>Deprecate feature <code>log</code> (<a href="">#1763</a>)</li>
</ul>
<p><a href="">#1761</a>: <a href="">rust-random/rand#1761</a>
<a href="">#1763</a>: <a href="">rust-random/rand#1763</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>27ff4cb</code></a> Prepare v0.10.1: deprecate feature <code>log</code> (<a href="">#1763</a>)</li>
<li><a href=""><code>98d0638</code></a> make_rng: document panic and add #[track_caller] (<a href="">#1761</a>)</li>
<li><a href=""><code>54e5eaa</code></a> Fix doc error (<a href="">#1758</a>)</li>
<li><a href=""><code>1ce4c08</code></a> Bump itoa from 1.0.17 to 1.0.18 in the all-deps group (<a href="">#1756</a>)</li>
<li><a href=""><code>ccb734b</code></a> docs: fix typo in doc comment (<a href="">#1754</a>)</li>
<li><a href=""><code>357eb7d</code></a> Bump libc from 0.2.182 to 0.2.183 in the all-deps group (<a href="">#1753</a>)</li>
<li><a href=""><code>5e77fe5</code></a> Fix trait references in documentation (<a href="">#1752</a>)</li>
<li><a href=""><code>da89185</code></a> Bump the all-deps group with 3 updates (<a href="">#1751</a>)</li>
<li><a href=""><code>50516ff</code></a> Bump the all-deps group with 2 updates (<a href="">#1749</a>)</li>
<li><a href=""><code>fd71de9</code></a> Bump the all-deps group with 2 updates (<a href="">#1747</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/rust-random/rand/compare/0.10.0...0.10.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=rand&package-manager=cargo&previous-version=0.10.0&new-version=0.10.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/sourmash-bio/sourmash/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `25221f4ad4c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.