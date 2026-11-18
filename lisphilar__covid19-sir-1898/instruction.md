# Issue

**Title:** build(deps-dev): update sphinx requirement from <8.0.0,>=7.2.6 to >=7.2.6,<9.0.0

## Description

Updates the requirements on [sphinx](https://github.com/sphinx-doc/sphinx) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-doc/sphinx/releases">sphinx's releases</a>.</em></p>
<blockquote>
<h2>Sphinx 8.1.3</h2>
<p>Changelog: <a href="https://www.sphinx-doc.org/en/master/changes/8.1.html">https://www.sphinx-doc.org/en/master/changes/8.1.html</a></p>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#13013</a>: Restore support for <code>cut_lines()</code> with no object type. Patch by Adam Turner.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-doc/sphinx/blob/v8.1.3/CHANGES.rst">sphinx's changelog</a>.</em></p>
<blockquote>
<h1>Release 8.1.3 (released Oct 13, 2024)</h1>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#13013</a>: Restore support for :func:<code>!cut_lines</code> with no object type.
Patch by Adam Turner.</li>
</ul>
<h1>Release 8.1.2 (released Oct 12, 2024)</h1>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#13012</a>: Expose :exc:<code>sphinx.errors.ExtensionError</code> in <code>sphinx.util</code>
for backwards compatibility.
This will be removed in Sphinx 9, as exposing the exception
in <code>sphinx.util</code> was never intentional.
:exc:<code>!ExtensionError</code> has been part of <code>sphinx.errors</code> since Sphinx 0.9.
Patch by Adam Turner.</li>
</ul>
<h1>Release 8.1.1 (released Oct 11, 2024)</h1>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#13006</a>: Use the preferred <a href="https://www.cve.org/">https://www.cve.org/</a> URL for
the :rst:role:<code>:cve: &lt;cve&gt;</code> role.
Patch by Hugo van Kemenade.</li>
<li><a href="">#13007</a>: LaTeX: Improve resiliency when the required
<code>fontawesome</code> or <code>fontawesome5</code> packages are not installed.
Patch by Jean-François B.</li>
</ul>
<h1>Release 8.1.0 (released Oct 10, 2024)</h1>
<h2>Dependencies</h2>
<ul>
<li><a href="">#12756</a>: Add lower-bounds to the <code>sphinxcontrib-*</code> dependencies.
Patch by Adam Turner.</li>
<li><a href="">#12833</a>: Update the LaTeX <code>parskip</code> package from 2001 to 2018.
Patch by Jean-François B.</li>
</ul>
<h2>Incompatible changes</h2>
<ul>
<li><a href="">#12763</a>: Remove unused internal class <code>sphinx.util.Tee</code>.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a1510de</code></a> Bump to 8.1.3 final</li>
<li><a href=""><code>62e9606</code></a> Restore support for <code>cut_lines()</code> with no object type (<a href="">#13015</a>)</li>
<li><a href=""><code>5ae32ce</code></a> Bump version</li>
<li><a href=""><code>a72b47b</code></a> Bump to 8.1.2 final</li>
<li><a href=""><code>39a45ad</code></a> Expose <code>ExtensionError</code> in <code>sphinx.util</code> for backwards compatibility.</li>
<li><a href=""><code>5a4859a</code></a> Add docs about sphinx-autobuild (<a href="">#13011</a>)</li>
<li><a href=""><code>05679ef</code></a> Type-check the 'autodoc_intenum' example (<a href="">#12827</a>)</li>
<li><a href=""><code>86d1d31</code></a> Prune CHANGES of unneeded sections</li>
<li><a href=""><code>b6269d3</code></a> Improve documentation for the Builder API (<a href="">#13008</a>)</li>
<li><a href=""><code>c46abc4</code></a> Improve clarity for <code>master_doc</code> and <code>root_doc</code></li>
<li>Additional commits viewable in <a href="https://github.com/sphinx-doc/sphinx/compare/v7.2.6...v8.1.3">compare view</a></li>
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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f71ed6810b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.