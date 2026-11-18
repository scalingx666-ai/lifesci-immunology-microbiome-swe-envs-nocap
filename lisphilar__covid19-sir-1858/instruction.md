# Issue

**Title:** build(deps): bump typing-extensions from 4.14.1 to 4.15.0

## Description

Bumps [typing-extensions](https://github.com/python/typing_extensions) from 4.14.1 to 4.15.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/releases">typing-extensions's releases</a>.</em></p>
<blockquote>
<h2>4.15.0</h2>
<p>No user-facing changes since 4.15.0rc1.</p>
<p>New features since 4.14.1:</p>
<ul>
<li>Add the <code>@typing_extensions.disjoint_base</code> decorator, as specified
in PEP 800. Patch by Jelle Zijlstra.</li>
<li>Add <code>typing_extensions.type_repr</code>, a backport of
<a href="https://docs.python.org/3.14/library/annotationlib.html#annotationlib.type_repr"><code>annotationlib.type_repr</code></a>,
introduced in Python 3.14 (CPython PR <a href="">#124551</a>,
originally by Jelle Zijlstra). Patch by Semyon Moroz.</li>
<li>Fix behavior of type params in <code>typing_extensions.evaluate_forward_ref</code>. Backport of
CPython PR <a href="">#137227</a> by Jelle Zijlstra.</li>
</ul>
<h2>4.15.0rc1</h2>
<ul>
<li>Add the <code>@typing_extensions.disjoint_base</code> decorator, as specified
in PEP 800. Patch by Jelle Zijlstra.</li>
<li>Add <code>typing_extensions.type_repr</code>, a backport of
<a href="https://docs.python.org/3.14/library/annotationlib.html#annotationlib.type_repr"><code>annotationlib.type_repr</code></a>,
introduced in Python 3.14 (CPython PR <a href="">#124551</a>,
originally by Jelle Zijlstra). Patch by Semyon Moroz.</li>
<li>Fix behavior of type params in <code>typing_extensions.evaluate_forward_ref</code>. Backport of
CPython PR <a href="">#137227</a> by Jelle Zijlstra.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/blob/main/CHANGELOG.md">typing-extensions's changelog</a>.</em></p>
<blockquote>
<h1>Release 4.15.0 (August 25, 2025)</h1>
<p>No user-facing changes since 4.15.0rc1.</p>
<h1>Release 4.15.0rc1 (August 18, 2025)</h1>
<ul>
<li>Add the <code>@typing_extensions.disjoint_base</code> decorator, as specified
in PEP 800. Patch by Jelle Zijlstra.</li>
<li>Add <code>typing_extensions.type_repr</code>, a backport of
<a href="https://docs.python.org/3.14/library/annotationlib.html#annotationlib.type_repr"><code>annotationlib.type_repr</code></a>,
introduced in Python 3.14 (CPython PR <a href="">#124551</a>,
originally by Jelle Zijlstra). Patch by Semyon Moroz.</li>
<li>Fix behavior of type params in <code>typing_extensions.evaluate_forward_ref</code>. Backport of
CPython PR <a href="">#137227</a> by Jelle Zijlstra.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9d1637e</code></a> Prepare release 4.15.0 (<a href="">#658</a>)</li>
<li><a href=""><code>4bd67c5</code></a> Coverage: exclude some noise (<a href="">#656</a>)</li>
<li><a href=""><code>e589a26</code></a> Coverage: add detailed report to job summary (<a href="">#655</a>)</li>
<li><a href=""><code>67d37fe</code></a> Coverage: Implement fail_under (<a href="">#654</a>)</li>
<li><a href=""><code>e9ae26f</code></a> Don't delete previous coverage comment (<a href="">#653</a>)</li>
<li><a href=""><code>ac80bb7</code></a> Add Coverage workflow (<a href="">#623</a>)</li>
<li><a href=""><code>abaaafd</code></a> Prepare release 4.15.0rc1 (<a href="">#650</a>)</li>
<li><a href=""><code>9810405</code></a> Add <code>@disjoint_base</code> (PEP 800) (<a href="">#634</a>)</li>
<li><a href=""><code>7ee9e05</code></a> Backport type_params fix from CPython (<a href="">#646</a>)</li>
<li><a href=""><code>1e8eb9c</code></a> Do not refer to PEP 705 as being experimental (<a href="">#648</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/typing_extensions/compare/4.14.1...4.15.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typing-extensions&package-manager=pip&previous-version=4.14.1&new-version=4.15.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `226894e24df2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.