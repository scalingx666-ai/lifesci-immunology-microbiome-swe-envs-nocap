# Issue

**Title:** Build(deps): Bump cfg-if from 1.0.0 to 1.0.1

## Description

Bumps [cfg-if](https://github.com/rust-lang/cfg-if) from 1.0.0 to 1.0.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/releases">cfg-if's releases</a>.</em></p>
<blockquote>
<h2>v1.0.1</h2>
<h3>Other</h3>
<ul>
<li>Remove <code>compiler-builtins</code> from <code>rustc-dep-of-std</code> dependencies</li>
<li>Remove redundant configuration from Cargo.toml</li>
<li>More readable formatting and identifier names. (<a href="">#39</a>)</li>
<li>Add expanded example to readme (<a href="">#38</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/rust-lang/cfg-if/blob/main/CHANGELOG.md">cfg-if's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/rust-lang/cfg-if/compare/v1.0.0...v1.0.1">1.0.1</a> - 2025-06-09</h2>
<h3>Other</h3>
<ul>
<li>Remove <code>compiler-builtins</code> from <code>rustc-dep-of-std</code> dependencies</li>
<li>Remove redundant configuration from Cargo.toml</li>
<li>More readable formatting and identifier names. (<a href="">#39</a>)</li>
<li>Add expanded example to readme (<a href="">#38</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dbfd663</code></a> chore: release v1.0.1</li>
<li><a href=""><code>1cc10c7</code></a> Remove <code>compiler-builtins</code> from <code>rustc-dep-of-std</code> dependencies</li>
<li><a href=""><code>0314c2b</code></a> ci: Fix the release job branch</li>
<li><a href=""><code>ee3062f</code></a> Remove redundant configuration from Cargo.toml</li>
<li><a href=""><code>3e3936e</code></a> cleanup: Remove trailing whitespace</li>
<li><a href=""><code>0f01eff</code></a> ci: Add a release job</li>
<li><a href=""><code>4edf327</code></a> Merge pull request <a href="">#83</a> from rust-lang/dependabot/github_actions/actions/check...</li>
<li><a href=""><code>d16050a</code></a> Bump actions/checkout from 4.2.1 to 4.2.2</li>
<li><a href=""><code>b01c675</code></a> Merge pull request <a href="">#82</a> from rust-lang/dependabot/github_actions/actions/check...</li>
<li><a href=""><code>fdd1c00</code></a> Bump actions/checkout from 4.2.0 to 4.2.1</li>
<li>Additional commits viewable in <a href="https://github.com/rust-lang/cfg-if/compare/1.0.0...v1.0.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=cfg-if&package-manager=cargo&previous-version=1.0.0&new-version=1.0.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be845125470d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.