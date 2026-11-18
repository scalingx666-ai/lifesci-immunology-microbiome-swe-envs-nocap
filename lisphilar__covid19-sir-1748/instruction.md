# Issue

**Title:** build(deps-dev): bump pyright from 1.1.381 to 1.1.382.post0

## Description

Bumps [pyright](https://github.com/RobertCraigie/pyright-python) from 1.1.381 to 1.1.382.post0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/RobertCraigie/pyright-python/releases">pyright's releases</a>.</em></p>
<blockquote>
<h2>v1.1.382.post0</h2>
<p>This release fixes a regression with <code>nodeenv</code> support in the <code>v1.1.382</code> release</p>
<h2>v1.1.382</h2>
<p>No release notes provided.</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c61cac8</code></a> chore: release v1.1.382.post0 (<a href="">#307</a>)</li>
<li><a href=""><code>f8e7383</code></a> CI: correct setup for nodeenv testing (<a href="">#306</a>)</li>
<li><a href=""><code>276e381</code></a> fix: correct nodeenv environment (<a href="">#305</a>)</li>
<li><a href=""><code>05e4563</code></a> Pyright NPM Package update to 1.1.382 (<a href="">#303</a>)</li>
<li><a href=""><code>0bf95f9</code></a> refactor(internal): switch to src dir (<a href="">#301</a>)</li>
<li><a href=""><code>f4beb25</code></a> feat(cli): mention nodejs extra if nodeenv install fails</li>
<li><a href=""><code>e2d0748</code></a> feat: add support for nodejs-wheel</li>
<li><a href=""><code>9edbff0</code></a> chore(internal): fix dev requirements</li>
<li><a href=""><code>a20dbee</code></a> chore(internal): remove unused npx target</li>
<li><a href=""><code>845c08e</code></a> chore(ci): add CI status job</li>
<li>Additional commits viewable in <a href="https://github.com/RobertCraigie/pyright-python/compare/v1.1.381...v1.1.382.post0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pyright&package-manager=pip&previous-version=1.1.381&new-version=1.1.382.post0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dd0c5086e53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.