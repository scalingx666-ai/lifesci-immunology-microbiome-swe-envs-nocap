# Issue

**Title:** build(deps-dev): bump ipywidgets from 8.1.6 to 8.1.7

## Description

Bumps [ipywidgets](https://github.com/jupyter-widgets/ipywidgets) from 8.1.6 to 8.1.7.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/jupyter-widgets/ipywidgets/releases">ipywidgets's releases</a>.</em></p>
<blockquote>
<h2>8.1.7</h2>
<h2>What's Changed</h2>
<ul>
<li>Fix CI + remove Python 3.8 by <a href="https://github.com/martinRenou"><code>@​martinRenou</code></a> in <a href="">jupyter-widgets/ipywidgets#3989</a></li>
<li>Dynamic widgets registry by <a href="https://github.com/martinRenou"><code>@​martinRenou</code></a> in <a href="">jupyter-widgets/ipywidgets#3988</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/jupyter-widgets/ipywidgets/compare/8.1.6...8.1.7">https://github.com/jupyter-widgets/ipywidgets/compare/8.1.6...8.1.7</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/jupyter-widgets/ipywidgets/compare/8.1.6...8.1.7">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ipywidgets&package-manager=pip&previous-version=8.1.6&new-version=8.1.7)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

## Summary by Sourcery

Build:
- Update poetry.lock to reflect ipywidgets version bump

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad62dc8f0884`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.