# Issue

**Title:** build(deps-dev): bump nbsphinx from 0.9.5 to 0.9.6

## Description

Bumps [nbsphinx](https://github.com/spatialaudio/nbsphinx) from 0.9.5 to 0.9.6.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/spatialaudio/nbsphinx/releases">nbsphinx's releases</a>.</em></p>
<blockquote>
<h2>nbsphinx 0.9.6</h2>
<p><a href="https://pypi.org/project/nbsphinx/0.9.6/">https://pypi.org/project/nbsphinx/0.9.6/</a></p>
<ul>
<li>Markdown: allow lists without leading blank line</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/spatialaudio/nbsphinx/blob/master/NEWS.rst">nbsphinx's changelog</a>.</em></p>
<blockquote>
<p>Version 0.9.6 -- 2024-12-24 -- PyPI__ -- diff__</p>
<ul>
<li>Markdown: allow lists without leading blank line</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.6/">https://pypi.org/project/nbsphinx/0.9.6/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.5...0.9.6">https://github.com/spatialaudio/nbsphinx/compare/0.9.5...0.9.6</a></p>
<p>Version 0.9.5 -- 2024-08-13 -- PyPI__ -- diff__</p>
<ul>
<li>Miscellaneous fixes</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.5/">https://pypi.org/project/nbsphinx/0.9.5/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.4...0.9.5">https://github.com/spatialaudio/nbsphinx/compare/0.9.4...0.9.5</a></p>
<p>Version 0.9.4 -- 2024-05-06 -- PyPI__ -- diff__</p>
<ul>
<li>Require <code>docutils &gt;= 0.18.1</code></li>
<li>Minor fixes, documentation and CI updates</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.4/">https://pypi.org/project/nbsphinx/0.9.4/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.3...0.9.4">https://github.com/spatialaudio/nbsphinx/compare/0.9.3...0.9.4</a></p>
<p>Version 0.9.3 -- 2023-08-27 -- PyPI__ -- diff__</p>
<ul>
<li>Fix gallery regression in Sphinx 7.2</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.3/">https://pypi.org/project/nbsphinx/0.9.3/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.2...0.9.3">https://github.com/spatialaudio/nbsphinx/compare/0.9.2...0.9.3</a></p>
<p>Version 0.9.2 -- 2023-05-24 -- PyPI__ -- diff__</p>
<ul>
<li>Improve support for <code>sphinx_immaterial</code> theme</li>
<li>Improve support for links starting with <code>#</code></li>
<li>Add support for in-text citations</li>
<li>LaTeX: Add support for admonition titles</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.2/">https://pypi.org/project/nbsphinx/0.9.2/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.1...0.9.2">https://github.com/spatialaudio/nbsphinx/compare/0.9.1...0.9.2</a></p>
<p>Version 0.9.1 -- 2023-03-14 -- PyPI__ -- diff__</p>
<ul>
<li>pandoc: disable &quot;smart&quot; option only for version 2.0+</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.1/">https://pypi.org/project/nbsphinx/0.9.1/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.0...0.9.1">https://github.com/spatialaudio/nbsphinx/compare/0.9.0...0.9.1</a></p>
<p>Version 0.9.0 -- 2023-03-12 -- PyPI__ -- diff__</p>
<ul>
<li>
<p>Split <code>nbsphinx.py</code> (a Python <em>module</em>) into:</p>
<ul>
<li><code>nbsphinx/__init__.py</code> (a Python <em>package</em>)</li>
<li>A standalone CSS file <code>nbsphinx-code-cells.css_t</code></li>
<li>LaTeX style file <code>nbsphinx.sty</code></li>
</ul>
</li>
<li>
<p>Add custom HTML/CSS for thumbnail galleries</p>
<ul>
<li>Separate CSS file <code>nbsphinx-gallery.css</code></li>
</ul>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>215bf0d</code></a> Release 0.9.6</li>
<li><a href=""><code>35686f5</code></a> DOC: Remove broken link</li>
<li><a href=""><code>837bea6</code></a> CI: ignore deprecated import_object</li>
<li><a href=""><code>40d8cd4</code></a> Use force=True with copyfile (<a href="">#819</a>)</li>
<li><a href=""><code>1fda481</code></a> DOC: add section about Xarray datasets</li>
<li><a href=""><code>84b9575</code></a> markdown: Fix bullet list parsing</li>
<li><a href=""><code>da82a07</code></a> CI: install rsvg-convert</li>
<li><a href=""><code>3a916b4</code></a> CI: remove .travis.yml</li>
<li><a href=""><code>52f2b34</code></a> CI: run with LaTeX and epub output</li>
<li><a href=""><code>8446fc5</code></a> CI: enable Python 3.13-dev</li>
<li>Additional commits viewable in <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.5...0.9.6">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=nbsphinx&package-manager=pip&previous-version=0.9.5&new-version=0.9.6)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump nbsphinx from 0.9.5 to 0.9.6.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13922de9a215`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.