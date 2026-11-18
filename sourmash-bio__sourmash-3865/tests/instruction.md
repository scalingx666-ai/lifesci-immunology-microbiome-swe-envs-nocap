# Issue

**Title:** Build(deps-py): Update sphinx requirement from <9,>=6 to >=6,<10 in the dependencies group

## Description

Updates the requirements on [sphinx](https://github.com/sphinx-doc/sphinx) to permit the latest version.
Updates `sphinx` to 9.0.1
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-doc/sphinx/releases">sphinx's releases</a>.</em></p>
<blockquote>
<h2>Sphinx 9.0.1</h2>
<p>Changelog: <a href="https://www.sphinx-doc.org/en/master/changes.html">https://www.sphinx-doc.org/en/master/changes.html</a></p>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#13942</a>: autodoc: Restore the mapping interface for options objects.
Patch by Adam Turner.</li>
<li><a href="">#13942</a>: autodoc: Deprecate the mapping interface for options objects.
Patch by Adam Turner.</li>
<li><a href="">#13387</a>: Update translations.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-doc/sphinx/blob/master/CHANGES.rst">sphinx's changelog</a>.</em></p>
<blockquote>
<h1>Release 9.0.1 (released Dec 01, 2025)</h1>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#13942</a>: autodoc: Restore the mapping interface for options objects.
Patch by Adam Turner.</li>
<li><a href="">#13942</a>: autodoc: Deprecate the mapping interface for options objects.
Patch by Adam Turner.</li>
<li><a href="">#13387</a>: Update translations.</li>
</ul>
<h1>Release 9.0.0 (released Nov 30, 2025)</h1>
<h2>Dependencies</h2>
<ul>
<li>
<p><a href="">#13786</a>: Support <code>Docutils 0.22</code>_. Patch by Adam Turner.</p>
<p>.. _Docutils 0.22: <a href="https://docutils.sourceforge.io/RELEASE-NOTES.html#release-0-22-2026-07-29">https://docutils.sourceforge.io/RELEASE-NOTES.html#release-0-22-2026-07-29</a></p>
</li>
</ul>
<h2>Incompatible changes</h2>
<ul>
<li><a href="">#13639</a>: :py:meth:<code>!SphinxComponentRegistry.create_source_parser</code> no longer
has an <em>app</em> parameter, instead taking <em>config</em> and <em>env</em>.
Patch by Adam Turner.</li>
<li><a href="">#13679</a>: Non-decodable characters in source files now raise an error.
Such bytes have been replaced with '?' along with logging a warning
since Sphinx 2.0.
Patch by Adam Turner.</li>
<li><a href="">#13751</a>, <a href="">#14089</a>: :mod:<code>sphinx.ext.autodoc</code> has been substantially rewritten,
and there may be some incompatible changes in edge cases, especially when
extensions interact with autodoc internals.
The :confval:<code>autodoc_use_legacy_class_based</code> option has been added to
use the legacy (pre-9.0) implementation of autodoc.
Patches by Adam Turner.</li>
<li><a href="">#13355</a>: Don't include escaped title content in the search index.
Patch by Will Lachance.</li>
</ul>
<h2>Deprecated</h2>
<ul>
<li>13627: Deprecate remaining public :py:attr:<code>!.app</code> attributes,
including <code>builder.app</code>, <code>env.app</code>, <code>events.app</code>,
and <code>SphinxTransform.app</code>.
Patch by Adam Turner.</li>
<li><a href="">#13637</a>: Deprecate the :py:meth:<code>!set_application</code> method
of :py:class:<code>~sphinx.parsers.Parser</code> objects.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a837378</code></a> Bump to 9.0.1 final</li>
<li><a href=""><code>48840e6</code></a> Note updated message catalogues in CHANGES</li>
<li><a href=""><code>5931339</code></a> [bot]: Update message catalogues (<a href="">#13387</a>)</li>
<li><a href=""><code>baffcf0</code></a> autodoc: Deprecate mapping interface for options (<a href="">#14140</a>)</li>
<li><a href=""><code>61f9b70</code></a> Bump mypy to 1.19.0 (<a href="">#14135</a>)</li>
<li><a href=""><code>ded587e</code></a> Shrink mypy whitelist for <code>tests.test_directives.test_directive_patch</code> (<a href="">#14</a>...</li>
<li><a href=""><code>a03556f</code></a> Shrink mypy whitelist for <code>tests.test_builders.test_build_latex</code> (<a href="">#14138</a>)</li>
<li><a href=""><code>0204145</code></a> linkcheck: Reduce test duration on Windows (<a href="">#14133</a>)</li>
<li><a href=""><code>4e902a4</code></a> Bump Ruff to 0.14.7 (<a href="">#14134</a>)</li>
<li><a href=""><code>9a11033</code></a> Bump version</li>
<li>Additional commits viewable in <a href="https://github.com/sphinx-doc/sphinx/compare/v6.0.0...v9.0.1">compare view</a></li>
</ul>
</details>
<br />

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
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45aec7430a6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.