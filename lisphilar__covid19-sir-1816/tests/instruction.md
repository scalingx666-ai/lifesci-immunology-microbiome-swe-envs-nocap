# Issue

**Title:** build(deps): bump typing-extensions from 4.12.2 to 4.13.2

## Description

Bumps [typing-extensions](https://github.com/python/typing_extensions) from 4.12.2 to 4.13.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/releases">typing-extensions's releases</a>.</em></p>
<blockquote>
<h2>4.13.2</h2>
<ul>
<li>Fix <code>TypeError</code> when taking the union of <code>typing_extensions.TypeAliasType</code> and a
<code>typing.TypeAliasType</code> on Python 3.12 and 3.13.
Patch by <a href="https://github.com/jorenham">Joren Hammudoglu</a>.</li>
<li>Backport from CPython PR <a href="">#132160</a>
to avoid having user arguments shadowed in generated <code>__new__</code> by
<code>@typing_extensions.deprecated</code>.
Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
</ul>
<h2>4.13.1</h2>
<p>This is a bugfix release fixing two edge cases that appear on old bugfix releases of CPython.</p>
<p>Bugfixes:</p>
<ul>
<li>Fix regression in 4.13.0 on Python 3.10.2 causing a <code>TypeError</code> when using <code>Concatenate</code>.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Fix <code>TypeError</code> when using <code>evaluate_forward_ref</code> on Python 3.10.1-2 and 3.9.8-10.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
</ul>
<h2>4.13.0</h2>
<p>New features:</p>
<ul>
<li>Add <code>typing_extensions.TypeForm</code> from PEP 747. Patch by
Jelle Zijlstra.</li>
<li>Add <code>typing_extensions.get_annotations</code>, a backport of
<code>inspect.get_annotations</code> that adds features specified
by PEP 649. Patches by Jelle Zijlstra and Alex Waygood.</li>
<li>Backport <code>evaluate_forward_ref</code> from CPython PR
<a href="">#119891</a> to evaluate <code>ForwardRef</code>s.
Patch by <a href="https://github.com/Daraan">Daraan</a>, backporting a CPython PR by Jelle Zijlstra.</li>
</ul>
<p>Bugfixes and changed features:</p>
<ul>
<li>Update PEP 728 implementation to a newer version of the PEP. Patch by Jelle Zijlstra.</li>
<li>Copy the coroutine status of functions and methods wrapped
with <code>@typing_extensions.deprecated</code>. Patch by Sebastian Rittau.</li>
<li>Fix bug where <code>TypeAliasType</code> instances could be subscripted even
where they were not generic. Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Fix bug where a subscripted <code>TypeAliasType</code> instance did not have all
attributes of the original <code>TypeAliasType</code> instance on older Python versions.
Patch by <a href="https://github.com/Daraan">Daraan</a> and Alex Waygood.</li>
<li>Fix bug where subscripted <code>TypeAliasType</code> instances (and some other
subscripted objects) had wrong parameters if they were directly
subscripted with an <code>Unpack</code> object.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Backport to Python 3.10 the ability to substitute <code>...</code> in generic <code>Callable</code>
aliases that have a <code>Concatenate</code> special form as their argument.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Extended the <code>Concatenate</code> backport for Python 3.8-3.10 to now accept
<code>Ellipsis</code> as an argument. Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Fix backport of <code>get_type_hints</code> to reflect Python 3.11+ behavior which does not add</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/python/typing_extensions/blob/main/CHANGELOG.md">typing-extensions's changelog</a>.</em></p>
<blockquote>
<h1>Release 4.13.2 (April 10, 2025)</h1>
<ul>
<li>Fix <code>TypeError</code> when taking the union of <code>typing_extensions.TypeAliasType</code> and a
<code>typing.TypeAliasType</code> on Python 3.12 and 3.13.
Patch by <a href="https://github.com/jorenham">Joren Hammudoglu</a>.</li>
<li>Backport from CPython PR <a href="">#132160</a>
to avoid having user arguments shadowed in generated <code>__new__</code> by
<code>@typing_extensions.deprecated</code>.
Patch by <a href="https://github.com/Viicos">Victorien Plot</a>.</li>
</ul>
<h1>Release 4.13.1 (April 3, 2025)</h1>
<p>Bugfixes:</p>
<ul>
<li>Fix regression in 4.13.0 on Python 3.10.2 causing a <code>TypeError</code> when using <code>Concatenate</code>.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Fix <code>TypeError</code> when using <code>evaluate_forward_ref</code> on Python 3.10.1-2 and 3.9.8-10.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
</ul>
<h1>Release 4.13.0 (March 25, 2025)</h1>
<p>No user-facing changes since 4.13.0rc1.</p>
<h1>Release 4.13.0rc1 (March 18, 2025)</h1>
<p>New features:</p>
<ul>
<li>Add <code>typing_extensions.TypeForm</code> from PEP 747. Patch by
Jelle Zijlstra.</li>
<li>Add <code>typing_extensions.get_annotations</code>, a backport of
<code>inspect.get_annotations</code> that adds features specified
by PEP 649. Patches by Jelle Zijlstra and Alex Waygood.</li>
<li>Backport <code>evaluate_forward_ref</code> from CPython PR
<a href="">#119891</a> to evaluate <code>ForwardRef</code>s.
Patch by <a href="https://github.com/Daraan">Daraan</a>, backporting a CPython PR by Jelle Zijlstra.</li>
</ul>
<p>Bugfixes and changed features:</p>
<ul>
<li>Update PEP 728 implementation to a newer version of the PEP. Patch by Jelle Zijlstra.</li>
<li>Copy the coroutine status of functions and methods wrapped
with <code>@typing_extensions.deprecated</code>. Patch by Sebastian Rittau.</li>
<li>Fix bug where <code>TypeAliasType</code> instances could be subscripted even
where they were not generic. Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Fix bug where a subscripted <code>TypeAliasType</code> instance did not have all
attributes of the original <code>TypeAliasType</code> instance on older Python versions.
Patch by <a href="https://github.com/Daraan">Daraan</a> and Alex Waygood.</li>
<li>Fix bug where subscripted <code>TypeAliasType</code> instances (and some other
subscripted objects) had wrong parameters if they were directly
subscripted with an <code>Unpack</code> object.
Patch by <a href="https://github.com/Daraan">Daraan</a>.</li>
<li>Backport to Python 3.10 the ability to substitute <code>...</code> in generic <code>Callable</code></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4525e9d</code></a> Prepare release 4.13.2 (<a href="">#583</a>)</li>
<li><a href=""><code>88a0c20</code></a> Do not shadow user arguments in generated <code>__new__</code> by <code>@deprecated</code> (<a href="">#581</a>)</li>
<li><a href=""><code>281d7b0</code></a> Add 3rd party tests for litestar (<a href="">#578</a>)</li>
<li><a href=""><code>8092c39</code></a> fix <code>TypeAliasType</code> union with <code>typing.TypeAliasType</code> (<a href="">#575</a>)</li>
<li><a href=""><code>45a8847</code></a> Prepare release 4.13.1 (<a href="">#573</a>)</li>
<li><a href=""><code>f264e58</code></a> Move CI to &quot;ubuntu-latest&quot; (round 2) (<a href="">#570</a>)</li>
<li><a href=""><code>5ce0e69</code></a> Fix TypeError with evaluate_forward_ref on some 3.10 and 3.9 versions (<a href="">#558</a>)</li>
<li><a href=""><code>304f5cb</code></a> Add SQLAlchemy to third-party daily tests (<a href="">#561</a>)</li>
<li><a href=""><code>ebe2b94</code></a> Fix duplicated keywords for typing._ConcatenateGenericAlias in 3.10.2 (<a href="">#557</a>)</li>
<li><a href=""><code>9f93d6f</code></a> Add intersphinx links for 3.13 typing features (<a href="">#550</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/python/typing_extensions/compare/4.12.2...4.13.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typing-extensions&package-manager=pip&previous-version=4.12.2&new-version=4.13.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump typing-extensions package from version 4.12.2 to 4.13.2 in the project dependencies

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d45789eacd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.