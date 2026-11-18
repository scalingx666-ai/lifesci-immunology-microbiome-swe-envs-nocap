# Issue

**Title:** build(deps): update tabulate requirement from <0.10.0,>=0.9.0 to >=0.9.0,<0.11.0

## Description

Updates the requirements on [tabulate](https://github.com/astanin/python-tabulate) to permit the latest version.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/astanin/python-tabulate/blob/master/CHANGELOG">tabulate's changelog</a>.</em></p>
<blockquote>
<ul>
<li>0.10.0: Add support for Python 3.11, 3.12, 3.13.
Drop support for Python 3.7, 3.8.
PRESERVE_STERILITY global is replaced with preserve_sterility function argument.
New formatting options: headersglobalalign, headersalign, colglobalalign.
New output format: <code>colon_grid</code> (Pandoc grid_tables with alignment)
Various bug fixes.
Improved error messages.</li>
<li>0.9.0: Drop support for Python 2.7, 3.5, 3.6.
Migrate to pyproject.toml project layout (PEP 621).
New output formats: <code>asciidoc</code>, various <code>*grid</code> and <code>*outline</code> formats.
New output features: vertical row alignment, separating lines.
New input format: list of dataclasses (Python 3.7 or later).
Support infinite iterables as row indices.
Improve column width options.
Improve support for ANSI escape sequences and document the behavior.
Various bug fixes.</li>
<li>0.8.10: Python 3.10 support. Bug fixes. Column width parameter.</li>
<li>0.8.9: Bug fix. Revert support of decimal separators.</li>
<li>0.8.8: Python 3.9 support, 3.10 ready.
New formats: <code>unsafehtml</code>, <code>latex_longtable</code>, <code>fancy_outline</code>.
Support lists of UserDicts as input.
Support hyperlinks in terminal output.
Improve testing on systems with proxies.
Migrate to pytest.
Various bug fixes and improvements.</li>
<li>0.8.7: Bug fixes. New format: <code>pretty</code>. HTML escaping.</li>
<li>0.8.6: Bug fixes. Stop supporting Python 3.3, 3.4.</li>
<li>0.8.5: Fix broken Windows package. Minor documentation updates.</li>
<li>0.8.4: Bug fixes.</li>
<li>0.8.3: New formats: <code>github</code>. Custom column alignment. Bug fixes.</li>
<li>0.8.2: Bug fixes.</li>
<li>0.8.1: Multiline data in several output formats.
New <code>latex_raw</code> format.
Column-specific floating point formatting.
Python 3.5 &amp; 3.6 support. Drop support for Python 2.6, 3.2, 3.3 (should still work).</li>
<li>0.7.7: Identical to 0.7.6, resolving some PyPI issues.</li>
<li>0.7.6: Bug fixes. New table formats (<code>psql</code>, <code>jira</code>, <code>moinmoin</code>, <code>textile</code>).
Wide character support. Printing from database cursors.
Option to print row indices. Boolean columns. Ragged rows.
Option to disable number parsing.</li>
<li>0.7.5: Bug fixes. <code>--float</code> format option for the command line utility.</li>
<li>0.7.4: Bug fixes. <code>fancy_grid</code> and <code>html</code> formats. Command line utility.</li>
<li>0.7.3: Bug fixes. Python 3.4 support. Iterables of dicts. <code>latex_booktabs</code> format.</li>
<li>0.7.2: Python 3.2 support.</li>
<li>0.7.1: Bug fixes. <code>tsv</code> format. Column alignment can be disabled.</li>
<li>0.7:   <code>latex</code> tables. Printing lists of named tuples and NumPy
record arrays. Fix printing date and time values. Python &lt;= 2.6.4 is supported.</li>
<li>0.6:   <code>mediawiki</code> tables, bug fixes.</li>
<li>0.5.1: Fix README.rst formatting. Optimize (performance similar to 0.4.4).</li>
<li>0.5:   ANSI color sequences. Printing dicts of iterables and Pandas' dataframes.</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3b4cd50</code></a> update HOWTOPUBLISH</li>
<li><a href=""><code>35ee0f6</code></a> update mini-benchmark table</li>
<li><a href=""><code>37ac76e</code></a> restore tabulate.<strong>version</strong></li>
<li><a href=""><code>37e1ed0</code></a> move # nowa: E931 to a different line (flake8)</li>
<li><a href=""><code>7bacc90</code></a> run pre-commit hooks (black)</li>
<li><a href=""><code>1b69704</code></a> Remove spurious cast in string interpolation</li>
<li><a href=""><code>4d535af</code></a> Use specific noqa directives</li>
<li><a href=""><code>76c3d37</code></a> Remove spurious space from error message</li>
<li><a href=""><code>13508e7</code></a> Unnecessary <code>list</code> call</li>
<li><a href=""><code>69f67cd</code></a> Do not call <code>getattr</code> with a constant value</li>
<li>Additional commits viewable in <a href="https://github.com/astanin/python-tabulate/compare/v0.9.0...v0.10.0">compare view</a></li>
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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a5e9fcb2cc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.