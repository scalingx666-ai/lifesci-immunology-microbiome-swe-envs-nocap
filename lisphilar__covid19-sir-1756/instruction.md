# Issue

**Title:** build(deps-dev): bump sphinx-rtd-theme from 2.0.0 to 3.0.0

## Description

Bumps [sphinx-rtd-theme](https://github.com/readthedocs/sphinx_rtd_theme) from 2.0.0 to 3.0.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/readthedocs/sphinx_rtd_theme/blob/master/docs/changelog.rst">sphinx-rtd-theme's changelog</a>.</em></p>
<blockquote>
<h1>3.0.0</h1>
<p>Final version.</p>
<p>.. _release-3.0.0rc4:</p>
<h1>3.0.0rc4</h1>
<h2>Fixes</h2>
<ul>
<li>Trigger &quot;Read the Docs Search addon&quot; when focusing the &quot;Search docs&quot; input in the navbar.</li>
</ul>
<p>.. _release-3.0.0rc3:</p>
<h1>3.0.0rc3</h1>
<h2>Fixes</h2>
<ul>
<li>Show hidden version in selector if it's the current active version</li>
</ul>
<p>.. _release-3.0.0rc2:</p>
<h1>3.0.0rc2</h1>
<h2>Added</h2>
<ul>
<li>Render version and language selectors below the documentation's title (top left).
This can be controlled via the new theme options <code>version_selector</code> and <code>language_selector</code>.</li>
</ul>
<p>.. _release-3.0.0rc1:</p>
<h1>3.0.0rc1</h1>
<h2>Added</h2>
<ul>
<li>Added support for Sphinx 8.</li>
<li>Added support for Python 3.12.</li>
<li>Added support for docutils <code>&gt;0.18, &lt;0.22</code>.</li>
<li>Populate <code>html_context</code> with all the environment variables starting with <code>READTHEDOCS_</code>.</li>
</ul>
<p>Deprecations</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a1c2147</code></a> Release 3.0.0</li>
<li><a href=""><code>814686e</code></a> Release 3.0.0rc4</li>
<li><a href=""><code>5b181b8</code></a> Trigger search modal on &quot;Search docs&quot; input focus (<a href="">#1610</a>)</li>
<li><a href=""><code>7deb68f</code></a> Release 3.0.0rc3</li>
<li><a href=""><code>036a3b2</code></a> Show hidden version in selector if it's the current active version (<a href="">#1609</a>)</li>
<li><a href=""><code>ccf3114</code></a> Release 3.0.0rc2 (<a href="">#1607</a>)</li>
<li><a href=""><code>4cab02f</code></a> Show version/language selectors below the title (<a href="">#1601</a>)</li>
<li><a href=""><code>9c75444</code></a> Docs: do not sign Git tag (<a href="">#1596</a>)</li>
<li><a href=""><code>3a3473d</code></a> Release 3.0.0rc1 (<a href="">#1597</a>)</li>
<li><a href=""><code>6b587d1</code></a> Prepare for 3.0 release (<a href="">#1576</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/readthedocs/sphinx_rtd_theme/compare/2.0.0...3.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=sphinx-rtd-theme&package-manager=pip&previous-version=2.0.0&new-version=3.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `432914403068`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.