# Issue

**Title:** Build(deps): Bump criterion from 0.6.0 to 0.7.0

## Description

Bumps [criterion](https://github.com/bheisler/criterion.rs) from 0.6.0 to 0.7.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/bheisler/criterion.rs/blob/master/CHANGELOG.md">criterion's changelog</a>.</em></p>
<blockquote>
<h2>[0.7.0] - 2025-07-25</h2>
<ul>
<li>Bump version of criterion-plot to align dependencies.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>567405d</code></a> release: bump criterion and criterion-plot versions (<a href="">#878</a>)</li>
<li><a href=""><code>ccccbcc</code></a> fix: deal with throughput in bits (<a href="">#861</a>)</li>
<li><a href=""><code>deb0eb0</code></a> feat: support throughput reports in bits (<a href="">#833</a>)</li>
<li><a href=""><code>d4fd7cc</code></a> Add CI job checking library builds with oldest allowed dependencies (<a href="">#854</a>)</li>
<li>See full diff in <a href="https://github.com/bheisler/criterion.rs/compare/0.6.0...0.7.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=criterion&package-manager=cargo&previous-version=0.6.0&new-version=0.7.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3b9281cb367`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.