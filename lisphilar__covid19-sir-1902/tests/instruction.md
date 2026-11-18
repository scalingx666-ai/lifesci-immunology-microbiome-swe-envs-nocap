# Issue

**Title:** build(deps-dev): update sphinx requirement from <9.0.0,>=7.2.6 to >=7.2.6,<10.0.0

## Description

Updates the requirements on [sphinx](https://github.com/sphinx-doc/sphinx) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-doc/sphinx/releases">sphinx's releases</a>.</em></p>
<blockquote>
<h2>Sphinx 9.1.0</h2>
<p>Changelog: <a href="https://www.sphinx-doc.org/en/master/changes.html">https://www.sphinx-doc.org/en/master/changes.html</a></p>
<h2>Dependencies</h2>
<ul>
<li><a href="">#14153</a>: Drop Python 3.11 support.</li>
<li><a href="">#12555</a>: Drop Docutils 0.20 support.
Patch by Adam Turner</li>
</ul>
<h2>Features added</h2>
<ul>
<li>Add <code>add_static_dir()</code> for copying static
assets from extensions to the build output.
Patch by Jared Dillard</li>
</ul>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#14189</a>: autodoc: Fix duplicate <code>:no-index-entry:</code> for modules.
Patch by Adam Turner</li>
<li><a href="">#13713</a>: Fix compatibility with MyST-Parser.
Patch by Adam Turner</li>
<li>Fix tests for Python 3.15.
Patch by Adam Turner</li>
<li><a href="">#14089</a>: autodoc: Fix default option parsing.
Patch by Adam Turner</li>
<li>Remove incorrect static typing assertions.
Patch by Adam Turner</li>
<li><a href="">#14050</a>: LaTeXTranslator fails to build documents using the &quot;acronym&quot;
standard role.
Patch by Günter Milde</li>
<li>LaTeX: Fix rendering for grid filled merged vertical cell.
Patch by Tim Nordell</li>
<li><a href="">#14228</a>: LaTeX: Fix overrun footer for cases of merged vertical table cells.
Patch by Tim Nordell</li>
<li><a href="">#14207</a>: Fix creating <code>HTMLThemeFactory</code> objects in third-party extensions.
Patch by Adam Turner</li>
<li><a href="">#3099</a>: LaTeX: PDF build crashes if a code-block contains more than
circa 1350 codelines (about 27 a4-sized pages at default pointsize).
Patch by Jean-François B.</li>
<li><a href="">#14064</a>: LaTeX: TABs ending up in sphinxVerbatim fail to obey tab stops.
Patch by Jean-François B.</li>
<li><a href="">#14089</a>: autodoc: Improve support for non-weakreferencable objects.
Patch by Adam Turner</li>
<li>LaTeX: Fix accidental removal at <code>3.5.0</code> (<a href="">#8854</a>) of the documentation of
<code>literalblockcappos</code> key of  sphinxsetup.
Patch by Jean-François B.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/sphinx-doc/sphinx/blob/master/CHANGES.rst">sphinx's changelog</a>.</em></p>
<blockquote>
<h1>Release 9.1.0 (released Dec 31, 2025)</h1>
<h2>Dependencies</h2>
<ul>
<li><a href="">#14153</a>: Drop Python 3.11 support.</li>
<li><a href="">#12555</a>: Drop Docutils 0.20 support.
Patch by Adam Turner</li>
</ul>
<h2>Features added</h2>
<ul>
<li>Add :meth:<code>~sphinx.application.Sphinx.add_static_dir</code> for copying static
assets from extensions to the build output.
Patch by Jared Dillard</li>
</ul>
<h2>Bugs fixed</h2>
<ul>
<li><a href="">#14189</a>: autodoc: Fix duplicate <code>:no-index-entry:</code> for modules.
Patch by Adam Turner</li>
<li><a href="">#13713</a>: Fix compatibility with MyST-Parser.
Patch by Adam Turner</li>
<li>Fix tests for Python 3.15.
Patch by Adam Turner</li>
<li><a href="">#14089</a>: autodoc: Fix default option parsing.
Patch by Adam Turner</li>
<li>Remove incorrect static typing assertions.
Patch by Adam Turner</li>
<li><a href="">#14050</a>: LaTeXTranslator fails to build documents using the &quot;acronym&quot;
standard role.
Patch by Günter Milde</li>
<li>LaTeX: Fix rendering for grid filled merged vertical cell.
Patch by Tim Nordell</li>
<li><a href="">#14228</a>: LaTeX: Fix overrun footer for cases of merged vertical table cells.
Patch by Tim Nordell</li>
<li><a href="">#14207</a>: Fix creating <code>HTMLThemeFactory</code> objects in third-party extensions.
Patch by Adam Turner</li>
<li><a href="">#3099</a>: LaTeX: PDF build crashes if a code-block contains more than
circa 1350 codelines (about 27 a4-sized pages at default pointsize).
Patch by Jean-François B.</li>
<li><a href="">#14064</a>: LaTeX: TABs ending up in sphinxVerbatim fail to obey tab stops.
Patch by Jean-François B.</li>
<li><a href="">#14089</a>: autodoc: Improve support for non-weakreferencable objects.
Patch by Adam Turner</li>
<li>LaTeX: Fix accidental removal at <code>3.5.0</code> (<a href="">#8854</a>) of the documentation of
<code>literalblockcappos</code> key of  :ref:<code>'sphinxsetup' &lt;latexsphinxsetup&gt;</code>.
Patch by Jean-François B.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>cc7c6f4</code></a> Bump to 9.1.0 final</li>
<li><a href=""><code>b127b94</code></a> Add <code>app.add_static_dir()</code> for copying extension static files (<a href="">#14219</a>)</li>
<li><a href=""><code>20f1c46</code></a> LaTeX: Inhibit breaks for rows with merged vertical cells (<a href="">#14227</a>)</li>
<li><a href=""><code>3c85411</code></a> Polish CHANGES.rst (<a href="">#14225</a>)</li>
<li><a href=""><code>9ee5446</code></a> LaTeX: restore 1.7 documentation of literalblockcappos (<a href="">#14224</a>)</li>
<li><a href=""><code>d75d602</code></a> LaTeX: improve (again...) some code comments in time for 9.1.0 (<a href="">#14222</a>)</li>
<li><a href=""><code>8dca61d</code></a> Improve some LaTeX code comments (<a href="">#14220</a>)</li>
<li><a href=""><code>8ab9600</code></a> Bump to 9.1.0 candidate 2</li>
<li><a href=""><code>d59b237</code></a> autodoc: Improve support for non-weakreferencable objects</li>
<li><a href=""><code>964424b</code></a> Use the correct reference for using existing extensions (<a href="">#14157</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/sphinx-doc/sphinx/compare/v7.2.6...v9.1.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d70b5288f75d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.