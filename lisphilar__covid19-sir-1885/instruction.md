# Issue

**Title:** build(deps-dev): bump nbsphinx from 0.9.7 to 0.9.8

## Description

Bumps [nbsphinx](https://github.com/spatialaudio/nbsphinx) from 0.9.7 to 0.9.8.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/spatialaudio/nbsphinx/releases">nbsphinx's releases</a>.</em></p>
<blockquote>
<h2>nbsphinx 0.9.8</h2>
<p><a href="https://pypi.org/project/nbsphinx/0.9.8/">https://pypi.org/project/nbsphinx/0.9.8/</a></p>
<ul>
<li>Re-enable Sphinx 8.2+</li>
<li>Support <code>text/x-rst</code> MIME type in raw cells</li>
<li>Support for <code>mathjax4_config</code></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/spatialaudio/nbsphinx/blob/master/NEWS.rst">nbsphinx's changelog</a>.</em></p>
<blockquote>
<p>Version 0.9.8 -- 2025-11-28 -- PyPI__ -- diff__</p>
<ul>
<li>Re-enable Sphinx 8.2+</li>
<li>Support <code>text/x-rst</code> MIME type in raw cells</li>
<li>Support for <code>mathjax4_config</code></li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.8/">https://pypi.org/project/nbsphinx/0.9.8/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.7...0.9.8">https://github.com/spatialaudio/nbsphinx/compare/0.9.7...0.9.8</a></p>
<p>Version 0.9.7 -- 2025-03-03 -- PyPI__ -- diff__</p>
<ul>
<li>Disable Sphinx 8.2+ (for now)</li>
</ul>
<p>__ <a href="https://pypi.org/project/nbsphinx/0.9.7/">https://pypi.org/project/nbsphinx/0.9.7/</a>
__ <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.6...0.9.7">https://github.com/spatialaudio/nbsphinx/compare/0.9.6...0.9.7</a></p>
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
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4f07420</code></a> Release 0.9.8</li>
<li><a href=""><code>75d6770</code></a> Avoid a logging error</li>
<li><a href=""><code>dd96f11</code></a> DOC: Update URL for the &lt;img&gt; element</li>
<li><a href=""><code>d97c011</code></a> Add support for mathjax4_config (<a href="">#854</a>)</li>
<li><a href=""><code>4882668</code></a> Fix nbsphinx_assume_equations to work with newer versions of Sphinx</li>
<li><a href=""><code>95372a7</code></a> CI: use &quot;uv&quot; for &quot;publish&quot; workflow</li>
<li><a href=""><code>9ce8c26</code></a> setup.py -&gt; pyproject.toml</li>
<li><a href=""><code>394b9ee</code></a> DOC: use anonymous hyperlinks for embedded URLs</li>
<li><a href=""><code>ab85921</code></a> Bump actions/upload-artifact from 4 to 5</li>
<li><a href=""><code>76122c2</code></a> Bump actions/download-artifact from 4 to 6</li>
<li>Additional commits viewable in <a href="https://github.com/spatialaudio/nbsphinx/compare/0.9.7...0.9.8">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=nbsphinx&package-manager=pip&previous-version=0.9.7&new-version=0.9.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `534bcf526832`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.