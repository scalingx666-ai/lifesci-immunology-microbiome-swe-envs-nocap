# Issue

**Title:** build(deps-dev): bump ipykernel from 6.30.0 to 6.30.1

## Description

Bumps [ipykernel](https://github.com/ipython/ipykernel) from 6.30.0 to 6.30.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ipython/ipykernel/releases">ipykernel's releases</a>.</em></p>
<blockquote>
<h2>v6.30.1</h2>
<h2>6.30.1</h2>
<p>This is a bugfix release to fix a significant bug introduced in 6.30.0 that allowed control messages to be handled concurrently rather than sequentially which broke debugging in JupyterLab and VSCode.</p>
<p>(<a href="https://github.com/ipython/ipykernel/compare/v6.30.0...357c908eab4ae97bb17c5dcabc7ee981df8ecb29">Full Changelog</a>)</p>
<h3>Bugs fixed</h3>
<ul>
<li>Correct use of asyncio.Lock to process a single control message at a time <a href="">#1416</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Backport: Remove links in changelog to github milestones that no longer exist <a href="">#1417</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/ipython/ipykernel/graphs/contributors?from=2025-07-21&amp;to=2025-08-04&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aianthomas23+updated%3A2025-07-21..2025-08-04&amp;type=Issues"><code>@​ianthomas23</code></a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ipython/ipykernel/blob/v6.30.1/CHANGELOG.md">ipykernel's changelog</a>.</em></p>
<blockquote>
<h2>6.30.1</h2>
<p>This is a bugfix release to fix a significant bug introduced in 6.30.0 that allowed control messages to be handled concurrently rather than sequentially which broke debugging in JupyterLab and VSCode.</p>
<p>(<a href="https://github.com/ipython/ipykernel/compare/v6.30.0...357c908eab4ae97bb17c5dcabc7ee981df8ecb29">Full Changelog</a>)</p>
<h3>Bugs fixed</h3>
<ul>
<li>Correct use of asyncio.Lock to process a single control message at a time <a href="">#1416</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Backport: Remove links in changelog to github milestones that no longer exist <a href="">#1417</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/ipython/ipykernel/graphs/contributors?from=2025-07-21&amp;to=2025-08-04&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aianthomas23+updated%3A2025-07-21..2025-08-04&amp;type=Issues"><code>@​ianthomas23</code></a></p>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>81587cc</code></a> Publish 6.30.1</li>
<li><a href=""><code>357c908</code></a> Correct use of asyncio.Lock to process a single control message at a time (<a href="">#1</a>...</li>
<li><a href=""><code>f96df51</code></a> Backport: Remove links in changelog to github milestones that no longer exist...</li>
<li>See full diff in <a href="https://github.com/ipython/ipykernel/compare/v6.30.0...v6.30.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ipykernel&package-manager=pip&previous-version=6.30.0&new-version=6.30.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dabea16ab316`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.