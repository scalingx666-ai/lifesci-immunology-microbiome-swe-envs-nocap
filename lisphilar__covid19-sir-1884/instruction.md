# Issue

**Title:** build(deps-dev): bump myst-parser from 3.0.1 to 4.0.1

## Description

Bumps [myst-parser](https://github.com/executablebooks/MyST-Parser) from 3.0.1 to 4.0.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/MyST-Parser/releases">myst-parser's releases</a>.</em></p>
<blockquote>
<h2>v4.0.1</h2>
<h2>What's Changed</h2>
<ul>
<li>
<p>🔧 Minor fix for sphinx 8.2 compat by <a href="https://github.com/chrisjsewell"><code>@​chrisjsewell</code></a> in <a href="">executablebooks/MyST-Parser#1013</a></p>
</li>
<li>
<p>🧪 Add CI testing support for Python 3.13 by <a href="https://github.com/hugovk"><code>@​hugovk</code></a> in <a href="">executablebooks/MyST-Parser#955</a></p>
</li>
<li>
<p>🔧 Fix type of MockIncludeDirective’s <code>klass</code> parameter by <a href="https://github.com/flying-sheep"><code>@​flying-sheep</code></a> in <a href="">executablebooks/MyST-Parser#975</a></p>
</li>
<li>
<p>📚 Fix typos discovered by codespell by <a href="https://github.com/cclauss"><code>@​cclauss</code></a> in <a href="">executablebooks/MyST-Parser#969</a></p>
</li>
<li>
<p>📚 remove redundant paragraph by <a href="https://github.com/Snoopy1866"><code>@​Snoopy1866</code></a> in <a href="">executablebooks/MyST-Parser#987</a></p>
</li>
<li>
<p>📚 Minor typo in <code>cross-referencing.md</code> by <a href="https://github.com/goekce"><code>@​goekce</code></a> in <a href="">executablebooks/MyST-Parser#990</a></p>
</li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/cclauss"><code>@​cclauss</code></a> made their first contribution in <a href="">executablebooks/MyST-Parser#969</a></li>
<li><a href="https://github.com/flying-sheep"><code>@​flying-sheep</code></a> made their first contribution in <a href="">executablebooks/MyST-Parser#975</a></li>
<li><a href="https://github.com/Snoopy1866"><code>@​Snoopy1866</code></a> made their first contribution in <a href="">executablebooks/MyST-Parser#987</a></li>
<li><a href="https://github.com/goekce"><code>@​goekce</code></a> made their first contribution in <a href="">executablebooks/MyST-Parser#990</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/executablebooks/MyST-Parser/compare/v4.0.0...v4.0.1">https://github.com/executablebooks/MyST-Parser/compare/v4.0.0...v4.0.1</a></p>
<h2>v4.0.0</h2>
<h2>What's Changed</h2>
<ul>
<li>⬆️ Support python&gt;=3.10, sphinx &gt;=7,&lt;9, docutils&gt;=0.19,&lt;0.22 by <a href="https://github.com/chrisjsewell"><code>@​chrisjsewell</code></a> in <a href="">executablebooks/MyST-Parser#952</a></li>
<li>👌 Improve footnote def/ref warnings and translations by <a href="https://github.com/chrisjsewell"><code>@​chrisjsewell</code></a> in <a href="">executablebooks/MyST-Parser#931</a></li>
<li>📚 Fix typo by <a href="https://github.com/meli-lewis"><code>@​meli-lewis</code></a> in <a href="">executablebooks/MyST-Parser#940</a></li>
</ul>
<h2>New Contributors</h2>
<ul>
<li><a href="https://github.com/meli-lewis"><code>@​meli-lewis</code></a> made their first contribution in <a href="">executablebooks/MyST-Parser#940</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/executablebooks/MyST-Parser/compare/v3.0.1...v4.0.0">https://github.com/executablebooks/MyST-Parser/compare/v3.0.1...v4.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/executablebooks/MyST-Parser/blob/master/CHANGELOG.md">myst-parser's changelog</a>.</em></p>
<blockquote>
<h2>4.0.1 - 2025-02-12</h2>
<p>🔧 Minor fix for Sphinx 8.2 compatibility (in <a href="gh-pr:1013">gh-pr:1013</a>)</p>
<h2>4.0.0 - 2024-08-05</h2>
<p>This release bumps the supported versions of:</p>
<ul>
<li>Python to <code>3.10</code> and greater</li>
<li>Sphinx to <code>&gt;=7,&lt;9</code></li>
<li>Docutils to <code>&gt;=0.19,&lt;0.22</code></li>
</ul>
<p>Additionally, footnotes are now parsed similar to the corresponding reStructuredText, in that resolution (between definitions and references) and ordering is now deferred to transforms on the doctree (in <a href="gh-pr:931">gh-pr:931</a>).</p>
<p>This allows for the proper interaction with other docutils/sphinx transforms, including those that perform translations,
and logging of warnings for duplicate/unreferenced footnote definitions and also for footnote references with no definitions.</p>
<p>See the <a href="https://github.com/executablebooks/MyST-Parser/blob/master/#syntax/footnotes">footnotes guide</a> for more information.</p>
<p><strong>Full Changelog</strong>: <a href="https://github.com/executablebooks/MyST-Parser/compare/v3.0.1...v4.0.0">v3.0.1...v4.0.0</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>8a44f5d</code></a> 🚀 Release v4.0.1 (<a href="">#1022</a>)</li>
<li><a href=""><code>fbb7f1d</code></a> 🔧 Minor fix for sphinx 8.2 compat (<a href="">#1013</a>)</li>
<li><a href=""><code>0437558</code></a> 🔧 update pre-commit (<a href="">#1006</a>)</li>
<li><a href=""><code>b58737f</code></a> ⬆️ Update pre-commit requirement from ~=3.0 to ~=4.0 (<a href="">#982</a>)</li>
<li><a href=""><code>f62025f</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#986</a>)</li>
<li><a href=""><code>14ea197</code></a> 📚 Minor typo in <code>cross-referencing.md</code> (<a href="">#990</a>)</li>
<li><a href=""><code>bc35794</code></a> 📚 remove redundant paragraph (<a href="">#987</a>)</li>
<li><a href=""><code>9fe724e</code></a> 🧪 Fix tests for latest sphinx (<a href="">#993</a>)</li>
<li><a href=""><code>59b5386</code></a> [pre-commit.ci] pre-commit autoupdate (<a href="">#976</a>)</li>
<li><a href=""><code>6bcba98</code></a> 🔧 Fix type of MockIncludeDirective’s <code>klass</code> parameter (<a href="">#975</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/executablebooks/MyST-Parser/compare/v3.0.1...v4.0.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=myst-parser&package-manager=pip&previous-version=3.0.1&new-version=4.0.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f5942813e65`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.