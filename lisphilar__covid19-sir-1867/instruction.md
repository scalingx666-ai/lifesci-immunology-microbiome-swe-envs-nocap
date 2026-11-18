# Issue

**Title:** build(deps-dev): bump ipykernel from 6.30.1 to 6.31.0

## Description

Bumps [ipykernel](https://github.com/ipython/ipykernel) from 6.30.1 to 6.31.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ipython/ipykernel/releases">ipykernel's releases</a>.</em></p>
<blockquote>
<h2>v6.31.0</h2>
<h2>6.31.0</h2>
<p>IPykernel 6.31.0 fixes an issue where display outputs such as Matplotlib plots were not included when using <code>%notebook</code> magic to save sessions as <code>.ipynb</code> files. This is enabled using the traitlet <code>ZMQDisplayPublisher.store_display_history</code> which defaults to the previous behaviour of <code>False</code>. This is a minor release rather than a patch release due to the addition of the new traitlet.</p>
<p>(<a href="https://github.com/ipython/ipykernel/compare/v6.30.1...01c1e8fe43047050f29d8728eabf4e4de14b624b">Full Changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>Backport PR <a href="">#1435</a>: Store display outputs in history for <code>%notebook</code> magic <a href="">#1461</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Backport PR <a href="">#1453</a>: update tests for 3.14 <a href="">#1460</a> (<a href="https://github.com/minrk"><code>@​minrk</code></a>)</li>
<li>Backport PR <a href="">#1444</a>: Test on PyPy 3.11 instead of 3.10 <a href="">#1459</a> (<a href="https://github.com/cclauss"><code>@​cclauss</code></a>)</li>
<li>6.x: Update PEP-639 license values in pyproject.toml <a href="">#1446</a> (<a href="https://github.com/bollwyvl"><code>@​bollwyvl</code></a>)</li>
<li>Backport PR <a href="">#1411</a>: Replace <code>@flaky.flaky</code> decorate with pytest fixture <a href="">#1421</a> (<a href="https://github.com/mgorny"><code>@​mgorny</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/ipython/ipykernel/graphs/contributors?from=2025-08-04&amp;to=2025-10-20&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Abollwyvl+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​bollwyvl</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Acclauss+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​cclauss</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3ADarshan808+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​Darshan808</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aianthomas23+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​ianthomas23</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Akrassowski+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​krassowski</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Alumberbot-app+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​lumberbot-app</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Ameeseeksmachine+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​meeseeksmachine</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Amgorny+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​mgorny</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aminrk+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​minrk</code></a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ipython/ipykernel/blob/v6.31.0/CHANGELOG.md">ipykernel's changelog</a>.</em></p>
<blockquote>
<h2>6.31.0</h2>
<p>IPykernel 6.31.0 fixes an issue where display outputs such as Matplotlib plots were not included when using <code>%notebook</code> magic to save sessions as <code>.ipynb</code> files. This is enabled using the traitlet <code>ZMQDisplayPublisher.store_display_history</code> which defaults to the previous behaviour of <code>False</code>. This is a minor release rather than a patch release due to the addition of the new traitlet.</p>
<p>(<a href="https://github.com/ipython/ipykernel/compare/v6.30.1...01c1e8fe43047050f29d8728eabf4e4de14b624b">Full Changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>Backport PR <a href="">#1435</a>: Store display outputs in history for <code>%notebook</code> magic <a href="">#1461</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Backport PR <a href="">#1453</a>: update tests for 3.14 <a href="">#1460</a> (<a href="https://github.com/minrk"><code>@​minrk</code></a>)</li>
<li>Backport PR <a href="">#1444</a>: Test on PyPy 3.11 instead of 3.10 <a href="">#1459</a> (<a href="https://github.com/cclauss"><code>@​cclauss</code></a>)</li>
<li>6.x: Update PEP-639 license values in pyproject.toml <a href="">#1446</a> (<a href="https://github.com/bollwyvl"><code>@​bollwyvl</code></a>)</li>
<li>Backport PR <a href="">#1411</a>: Replace <code>@flaky.flaky</code> decorate with pytest fixture <a href="">#1421</a> (<a href="https://github.com/mgorny"><code>@​mgorny</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/ipython/ipykernel/graphs/contributors?from=2025-08-04&amp;to=2025-10-20&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Abollwyvl+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​bollwyvl</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Acclauss+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​cclauss</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3ADarshan808+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​Darshan808</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aianthomas23+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​ianthomas23</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Akrassowski+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​krassowski</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Alumberbot-app+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​lumberbot-app</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Ameeseeksmachine+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​meeseeksmachine</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Amgorny+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​mgorny</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aminrk+updated%3A2025-08-04..2025-10-20&amp;type=Issues"><code>@​minrk</code></a></p>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>51272ac</code></a> Publish 6.31.0</li>
<li><a href=""><code>01c1e8f</code></a> Backport PR <a href="">#1435</a>: Store display outputs in history for <code>%notebook</code> magic (<a href="">#1</a>...</li>
<li><a href=""><code>e792ab9</code></a> Backport PR <a href="">#1453</a>: update tests for 3.14 (<a href="">#1460</a>)</li>
<li><a href=""><code>ddd77b7</code></a> Backport PR <a href="">#1444</a> on branch 6.x (ci: Test on PyPy 3.11 instead of 3.10) (<a href="">#1459</a>)</li>
<li><a href=""><code>675abf4</code></a> 6.x: Update PEP-639 license values in pyproject.toml (<a href="">#1446</a>)</li>
<li><a href=""><code>d208be4</code></a> Backport PR 1411 to 6.x (<a href="">#1421</a>)</li>
<li>See full diff in <a href="https://github.com/ipython/ipykernel/compare/v6.30.1...v6.31.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ipykernel&package-manager=pip&previous-version=6.30.1&new-version=6.31.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1cf695da3470`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.