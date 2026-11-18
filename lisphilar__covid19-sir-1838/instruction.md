# Issue

**Title:** build(deps): bump typing-extensions from 4.13.2 to 4.14.0

## Description

Bumps [typing-extensions](https://github.com/python/typing_extensions) from 4.13.2 to 4.14.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/releases">typing-extensions's releases</a>.</em></p>
<blockquote>
<h2>4.14.0</h2>
<p>This release adds several new features, including experimental support for inline typed dictionaries (<a href="https://peps.python.org/pep-0764/">PEP 764</a>) and sentinels (<a href="https://peps.python.org/pep-0661/">PEP 661</a>), and support for changes in Python 3.14. In addition, Python 3.8 is no longer supported.</p>
<p>Changes since 4.14.0rc1:</p>
<ul>
<li>Remove <code>__or__</code> and <code>__ror__</code> methods from <code>typing_extensions.Sentinel</code>
on Python versions &lt;3.10. PEP 604 was introduced in Python 3.10, and
<code>typing_extensions</code> does not generally attempt to backport PEP-604 methods
to prior versions.</li>
<li>Further update <code>typing_extensions.evaluate_forward_ref</code> with changes in Python 3.14.</li>
</ul>
<p>Changes included in 4.14.0rc1:</p>
<ul>
<li>Drop support for Python 3.8 (including PyPy-3.8). Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
<li>Do not attempt to re-export names that have been removed from <code>typing</code>,
anticipating the removal of <code>typing.no_type_check_decorator</code> in Python 3.15.
Patch by Jelle Zijlstra.</li>
<li>Update <code>typing_extensions.Format</code>, <code>typing_extensions.evaluate_forward_ref</code>, and
<code>typing_extensions.TypedDict</code> to align
with changes in Python 3.14. Patches by Jelle Zijlstra.</li>
<li>Fix tests for Python 3.14 and 3.15. Patches by Jelle Zijlstra.</li>
</ul>
<p>New features:</p>
<ul>
<li>Add support for inline typed dictionaries (<a href="https://peps.python.org/pep-0764/">PEP 764</a>).
Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
<li>Add <code>typing_extensions.Reader</code> and <code>typing_extensions.Writer</code>. Patch by
Sebastian Rittau.</li>
<li>Add support for sentinels (<a href="https://peps.python.org/pep-0661/">PEP 661</a>). Patch by
<a href="https://github.com/Viicos">Victorien Plot</a>.</li>
</ul>
<h2>4.14.0rc1</h2>
<p>Major changes:</p>
<ul>
<li>Drop support for Python 3.8 (including PyPy-3.8). Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
<li>Do not attempt to re-export names that have been removed from <code>typing</code>,
anticipating the removal of <code>typing.no_type_check_decorator</code> in Python 3.15.
Patch by Jelle Zijlstra.</li>
<li>Update <code>typing_extensions.Format</code>, <code>typing_extensions.evaluate_forward_ref</code>, and
<code>typing_extensions.TypedDict</code> to align
with changes in Python 3.14. Patches by Jelle Zijlstra.</li>
<li>Fix tests for Python 3.14 and 3.15. Patches by Jelle Zijlstra.</li>
</ul>
<p>New features:</p>
<ul>
<li>Add support for inline typed dictionaries (<a href="https://peps.python.org/pep-0764/">PEP 764</a>).
Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
<li>Add <code>typing_extensions.Reader</code> and <code>typing_extensions.Writer</code>. Patch by
Sebastian Rittau.</li>
<li>Add support for sentinels (<a href="https://peps.python.org/pep-0661/">PEP 661</a>). Patch by</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/blob/main/CHANGELOG.md">typing-extensions's changelog</a>.</em></p>
<blockquote>
<h1>Release 4.14.0 (June 2, 2025)</h1>
<p>Changes since 4.14.0rc1:</p>
<ul>
<li>Remove <code>__or__</code> and <code>__ror__</code> methods from <code>typing_extensions.Sentinel</code>
on Python versions &lt;3.10. PEP 604 was introduced in Python 3.10, and
<code>typing_extensions</code> does not generally attempt to backport PEP-604 methods
to prior versions.</li>
<li>Further update <code>typing_extensions.evaluate_forward_ref</code> with changes in Python 3.14.</li>
</ul>
<h1>Release 4.14.0rc1 (May 24, 2025)</h1>
<ul>
<li>Drop support for Python 3.8 (including PyPy-3.8). Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
<li>Do not attempt to re-export names that have been removed from <code>typing</code>,
anticipating the removal of <code>typing.no_type_check_decorator</code> in Python 3.15.
Patch by Jelle Zijlstra.</li>
<li>Update <code>typing_extensions.Format</code>, <code>typing_extensions.evaluate_forward_ref</code>, and
<code>typing_extensions.TypedDict</code> to align
with changes in Python 3.14. Patches by Jelle Zijlstra.</li>
<li>Fix tests for Python 3.14 and 3.15. Patches by Jelle Zijlstra.</li>
</ul>
<p>New features:</p>
<ul>
<li>Add support for inline typed dictionaries (<a href="https://peps.python.org/pep-0764/">PEP 764</a>).
Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
<li>Add <code>typing_extensions.Reader</code> and <code>typing_extensions.Writer</code>. Patch by
Sebastian Rittau.</li>
<li>Add support for sentinels (<a href="https://peps.python.org/pep-0661/">PEP 661</a>). Patch by
<a href="https://github.com/Viicos">Victorien Plot</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b07d245</code></a> Prepare release 4.14.0 (<a href="">#612</a>)</li>
<li><a href=""><code>fcf5265</code></a> Backport evaluate_forward_ref() changes (<a href="">#611</a>)</li>
<li><a href=""><code>fadc1ed</code></a> Remove PEP-604 methods from <code>Sentinel</code> on Python &lt;3.10 (<a href="">#605</a>)</li>
<li><a href=""><code>44de568</code></a> Add 3.14 to project classifiers and tox.ini (<a href="">#604</a>)</li>
<li><a href=""><code>36cc476</code></a> Prepare release 4.14.0rc1 (<a href="">#603</a>)</li>
<li><a href=""><code>ec1876c</code></a> More fixes for 3.14 and 3.15 (<a href="">#602</a>)</li>
<li><a href=""><code>e89d789</code></a> Update <code>_caller()</code> implementation (<a href="">#598</a>)</li>
<li><a href=""><code>34bfd84</code></a> third party: fix typeguard (<a href="">#600</a>)</li>
<li><a href=""><code>479dae1</code></a> Add support for sentinels (PEP 661) (<a href="">#594</a>)</li>
<li><a href=""><code>f74a56a</code></a> Update PEP 649/749 implementation (<a href="">#596</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/typing_extensions/compare/4.13.2...4.14.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typing-extensions&package-manager=pip&previous-version=4.13.2&new-version=4.14.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Bump typing-extensions to 4.14.0 in project dependencies to adopt the latest typing support and Python 3.14 compatibility.

Enhancements:
- Bring inline TypedDict (PEP 764), Reader/Writer types, and sentinel (PEP 661) support via typing-extensions
- Align type handling with Python 3.14 changes and drop Python 3.8 support in typing-extensions

Build:
- Update Poetry lockfile to require typing-extensions 4.14.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfba07928069`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.