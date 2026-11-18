# Issue

**Title:** Build(ci): Bump supercharge/redis-github-action from 1.8.0 to 1.8.1

## Description

Bumps [supercharge/redis-github-action](https://github.com/supercharge/redis-github-action) from 1.8.0 to 1.8.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/supercharge/redis-github-action/releases">supercharge/redis-github-action's releases</a>.</em></p>
<blockquote>
<h2>1.8.1</h2>
<p>Release 1.8.1</p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/supercharge/redis-github-action/blob/main/CHANGELOG.md">supercharge/redis-github-action's changelog</a>.</em></p>
<blockquote>
<h2><a href="https://github.com/supercharge/redis-github-action/compare/v1.8.0...v1.8.1">1.8.1</a> - 2025-11-12</h2>
<h3>Fixed</h3>
<ul>
<li>change Docker tag from <code>docker:stable</code> to <code>docker:latest</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bc274cb</code></a> prepare readme for 1.8.1</li>
<li><a href=""><code>a52dd79</code></a> prepare changelog for 1.8.1</li>
<li><a href=""><code>9c3a1cd</code></a> Merge pull request <a href="">#29</a> from supercharge/28-with-the-docker-v29-release-this-a...</li>
<li><a href=""><code>6991b77</code></a> switch from docker:stable to docker:latest</li>
<li><a href=""><code>f21a04d</code></a> Merge pull request <a href="">#27</a> from DhavalGojiya/bugfix/issue-26-redis-rm-flag-order</li>
<li><a href=""><code>f7760cc</code></a> [FIX] - Correct '--rm' argument placement in docker run (<a href="">#26</a>)</li>
<li><a href=""><code>0bc8516</code></a> add steps on how to create a new release for my future self</li>
<li>See full diff in <a href="https://github.com/supercharge/redis-github-action/compare/1.8.0...1.8.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=supercharge/redis-github-action&package-manager=github_actions&previous-version=1.8.0&new-version=1.8.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

You can trigger a rebase of this PR by commenting `@dependabot rebase`.

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

> **Note**
> Automatic rebases have been disabled on this pull request as it has been open for over 30 days.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce8219ab027f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.