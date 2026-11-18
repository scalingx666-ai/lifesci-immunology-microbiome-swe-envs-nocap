# Issue

**Title:** Build(deps): Bump serde_json from 1.0.140 to 1.0.141

## Description

Bumps [serde_json](https://github.com/serde-rs/json) from 1.0.140 to 1.0.141.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/serde-rs/json/releases">serde_json's releases</a>.</em></p>
<blockquote>
<h2>v1.0.141</h2>
<ul>
<li>Optimize string escaping during serialization (<a href="">#1273</a>, thanks <a href="https://github.com/conradludgate"><code>@​conradludgate</code></a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6843c36</code></a> Release 1.0.141</li>
<li><a href=""><code>6e2c210</code></a> Touch up PR 1273</li>
<li><a href=""><code>623d9b4</code></a> Merge pull request <a href="">#1273</a> from conradludgate/optimise-string-escaping</li>
<li><a href=""><code>de70b7d</code></a> use unreachable_unchecked for escape table. use a second match to roundtrip E...</li>
<li><a href=""><code>f2d940d</code></a> replace start index with bytes slice reference</li>
<li><a href=""><code>cd55b5a</code></a> Ignore mismatched_lifetime_syntaxes lint</li>
<li><a href=""><code>c1826eb</code></a> Pin nightly toolchain used for miri job</li>
<li><a href=""><code>8a56cfa</code></a> Merge pull request <a href="">#1248</a> from jimmycathy/master</li>
<li><a href=""><code>af3d80d</code></a> chore: fix typo</li>
<li>See full diff in <a href="https://github.com/serde-rs/json/compare/v1.0.140...v1.0.141">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=serde_json&package-manager=cargo&previous-version=1.0.140&new-version=1.0.141)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9bcf38381ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.