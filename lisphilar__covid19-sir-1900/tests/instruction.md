# Issue

**Title:** build(deps-dev): update docutils requirement from <0.22.0,>=0.20.1 to >=0.20.1,<0.23.0

## Description

Updates the requirements on [docutils](https://github.com/rtfd/recommonmark) to permit the latest version.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/readthedocs/recommonmark/blob/master/CHANGELOG.md">docutils's changelog</a>.</em></p>
<blockquote>
<h2>Development</h2>
<h2>Version 0.7.0</h2>
<p>Date: 2020-12-17</p>
<ul>
<li><a href="https://github.com/limasierra">limasierra</a>: Bugfix: External links to 'supported' files
lose their file extension (<a href="">#181</a>)</li>
</ul>
<h2>Version 0.6.0</h2>
<p>Date: 2019-08-09</p>
<ul>
<li><a href="http://github.com/RaptorCZ"><code>@​RaptorCZ</code></a>: Process linebreaks and
convert them to br element.
(<a href="">#162</a>)</li>
<li><a href="http://github.com/gibfahn"><code>@​gibfahn</code></a>: Remove URL quoting from refs
before passing to Sphinx
(<a href="">#158</a>)</li>
<li><a href="http://github.com/dandersson"><code>@​dandersson</code></a>: Use image description
text as &quot;alt&quot;, drop title
(<a href="">#150</a>)</li>
<li><a href="http://github.com/annegentle"><code>@​annegentle</code></a>: Clarify the specifics
of Auto Toc Tree
(<a href="">#149</a>)</li>
<li><a href="http://github.com/loganrosen"><code>@​loganrosen</code></a>: Bump dependency on
commonmark to &gt;= 0.8.1
(<a href="">#147</a>)</li>
<li><a href="http://github.com/codejamninja"><code>@​codejamninja</code></a>: Use official
gitignore template
(<a href="">#140</a>)</li>
<li><a href="http://github.com/dotlambda"><code>@​dotlambda</code></a>: Include all test files in
PyPI tarball
(<a href="">#128</a>)</li>
<li><a href="http://github.com/tk0miya"><code>@​tk0miya</code></a>: Register a parser class using
new Sphinx API; add_source_suffix
(<a href="">#113</a>)</li>
</ul>
<h2>Changelog</h2>
<h2>0.4.0 (in development)</h2>
<p>Set rawsource value for each nodes.</p>
<h2>0.3.0 (2016-01-15)</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/rtfd/recommonmark/commits">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a76ce940135`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.