# Issue

**Title:** build(deps-dev): bump ipykernel from 6.29.5 to 6.30.0

## Description

Bumps [ipykernel](https://github.com/ipython/ipykernel) from 6.29.5 to 6.30.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/ipython/ipykernel/releases">ipykernel's releases</a>.</em></p>
<blockquote>
<h2>v6.30.0</h2>
<h2>6.30.0</h2>
<p>This release fixes three bugs but is primarily a maintenance release bringing support for Python 3.13 and updating dependencies. It does not include subshells which will be in the upcoming 7.0.0 release. Users and downstream libraries that wish to avoid subshells should pin to <code>ipykernel &lt; 7</code>.</p>
<p>(<a href="https://github.com/ipython/ipykernel/compare/b1283b144...d9bd546a4dc49a41c3ad5fcc5d4a61f259973182">Full Changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>Remove control queue <a href="">#1210</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Bugs fixed</h3>
<ul>
<li>Set shell idle when message skipped by &quot;should_handle&quot; in &quot;dispatch_shell&quot; <a href="">#1395</a> (<a href="https://github.com/dby-tmwctw"><code>@​dby-tmwctw</code></a>)</li>
<li>Fixed error accessing sys.stdout/sys.stderr when those are None <a href="">#1247</a> (<a href="https://github.com/gregory-shklover"><code>@​gregory-shklover</code></a>)</li>
<li>Allow datetime or str in test_sequential_control_messages <a href="">#1219</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>6.x backports <a href="">#1406</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
<li>Update pre-commit and github actions <a href="">#1401</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
<li>Test more python versions on 6.x branch <a href="">#1398</a> (<a href="https://github.com/davidbrochart"><code>@​davidbrochart</code></a>)</li>
<li>Backports and extra changes to fix CI on 6.x branch <a href="">#1390</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
<li>Remove nose import. <a href="">#1368</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Test more python versions <a href="">#1358</a> (<a href="https://github.com/davidbrochart"><code>@​davidbrochart</code></a>)</li>
<li>Fix expected text depending on IPython version. <a href="">#1354</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Licence :: * trove classifers are deprecated <a href="">#1348</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Try to fix spyder kernel install <a href="">#1337</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Remove test_check job <a href="">#1335</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Don't rerun test with --lf it hides failures. <a href="">#1324</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Remove link to numfocus for funding. <a href="">#1320</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Remove downstream_check <a href="">#1318</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Copy payloadpage.page from IPython <a href="">#1317</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Remove base setup <a href="">#1299</a> (<a href="https://github.com/davidbrochart"><code>@​davidbrochart</code></a>)</li>
<li>Rely on intrsphinx_registry to keep intersphinx up to date. <a href="">#1290</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Drop support for Python 3.8 <a href="">#1284</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
<li>Start testing on 3.13 <a href="">#1277</a> (<a href="https://github.com/Carreau"><code>@​Carreau</code></a>)</li>
<li>Build docs on ubuntu <a href="">#1257</a> (<a href="https://github.com/blink1073"><code>@​blink1073</code></a>)</li>
<li>Avoid a DeprecationWarning on Python 3.13+ <a href="">#1248</a> (<a href="https://github.com/hroncok"><code>@​hroncok</code></a>)</li>
<li>Catch IPython 8.24 DeprecationWarnings <a href="">#1242</a> (<a href="https://github.com/s-t-e-v-e-n-k"><code>@​s-t-e-v-e-n-k</code></a>)</li>
<li>Add compat with pytest 8 <a href="">#1231</a> (<a href="https://github.com/blink1073"><code>@​blink1073</code></a>)</li>
<li>Set all min deps <a href="">#1229</a> (<a href="https://github.com/blink1073"><code>@​blink1073</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/ipython/ipykernel/graphs/contributors?from=2024-07-01&amp;to=2025-07-21&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3ACarreau+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​Carreau</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Accordoba12+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​ccordoba12</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Adavidbrochart+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​davidbrochart</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Adby-tmwctw+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​dby-tmwctw</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Agregory-shklover+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​gregory-shklover</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aianthomas23+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​ianthomas23</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aivanov+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​ivanov</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Ajasongrout+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​jasongrout</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Akrassowski+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​krassowski</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Ameeseeksmachine+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​meeseeksmachine</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aminrk+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​minrk</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Anathanmcavoy+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​nathanmcavoy</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3As-t-e-v-e-n-k+updated%3A2024-07-01..2025-07-21&amp;type=Issues"><code>@​s-t-e-v-e-n-k</code></a></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ipython/ipykernel/blob/main/CHANGELOG.md">ipykernel's changelog</a>.</em></p>
<blockquote>
<h2>6.30.0a0</h2>
<p>Pre-release to allow further testing of subshell implementation.</p>
<p>(<a href="https://github.com/ipython/ipykernel/compare/v6.29.5...5d90d9e10425886deb4b0f1676b14b1701522b3c">Full Changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>Subshells implemented using tornado event loops on 6.x branch <a href="">#1396</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
</ul>
<h3>Bugs fixed</h3>
<ul>
<li>[Bugfix] Set shell idle when message skipped by &quot;should_handle&quot; in &quot;dispatch_shell&quot; <a href="">#1395</a> (<a href="https://github.com/dby-tmwctw"><code>@​dby-tmwctw</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Backports and extra changes to fix CI on 6.x branch <a href="">#1390</a> (<a href="https://github.com/ianthomas23"><code>@​ianthomas23</code></a>)</li>
<li>Avoid a DeprecationWarning on Python 3.13+ <a href="">#1248</a> (<a href="https://github.com/hroncok"><code>@​hroncok</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/ipython/ipykernel/graphs/contributors?from=2024-07-01&amp;to=2025-06-05&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3ACarreau+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​Carreau</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Accordoba12+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​ccordoba12</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Adavidbrochart+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​davidbrochart</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Adby-tmwctw+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​dby-tmwctw</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aianthomas23+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​ianthomas23</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aivanov+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​ivanov</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Ajasongrout+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​jasongrout</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Akrassowski+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​krassowski</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Ameeseeksmachine+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​meeseeksmachine</code></a> | <a href="https://github.com/search?q=repo%3Aipython%2Fipykernel+involves%3Aminrk+updated%3A2024-07-01..2025-06-05&amp;type=Issues"><code>@​minrk</code></a></p>
<!-- raw HTML omitted -->
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>7f78f02</code></a> Publish 6.30.0</li>
<li><a href=""><code>d9bd546</code></a> 6.x backports (<a href="">#1406</a>)</li>
<li><a href=""><code>7603443</code></a> [Bugfix] Set shell idle when message skipped by &quot;should_handle&quot; in &quot;dispatch_...</li>
<li><a href=""><code>3c96ba2</code></a> Backports and extra changes to fix CI on 6.x branch (<a href="">#1390</a>)</li>
<li><a href=""><code>5d2fe53</code></a> Backport PR <a href="">#1248</a> on branch 6.x (Avoid a DeprecationWarning on Python 3.13+) ...</li>
<li>See full diff in <a href="https://github.com/ipython/ipykernel/compare/v6.29.5...v6.30.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=ipykernel&package-manager=pip&previous-version=6.29.5&new-version=6.30.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `894414260bda`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.