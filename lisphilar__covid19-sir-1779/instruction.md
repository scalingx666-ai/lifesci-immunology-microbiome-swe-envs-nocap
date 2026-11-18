# Issue

**Title:** build(deps-dev): bump pytest-profiling from 1.7.0 to 1.8.1

## Description

Bumps [pytest-profiling](https://github.com/man-group/pytest-plugins) from 1.7.0 to 1.8.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/man-group/pytest-plugins/releases">pytest-profiling's releases</a>.</em></p>
<blockquote>
<h2>1.8.1</h2>
<ul>
<li>All: Add a CircleCI Windows build with py3.6-py3.12 and remove references to TravisCI. (<a href="">#246</a>)</li>
<li>All: Add Ubuntu builds for py3.6-3.13</li>
<li>All: CircleCI release jobs now depend on both Ubuntu and Windows success.</li>
<li>pytest-listener: Use py_modules in setup.py</li>
<li>pytest-listener: Fix flakiness on py3.9+ on Windows when the receive time was equal to the clear_time.</li>
<li>pytest-profiling: Small refactor to make error messages a bit clearer</li>
<li>pytest-profiling: Fixed tests which were installing from PyPI rather than local</li>
<li>pytest-profiling: Removed usage of deprecated <code>pytest.yield_fixture</code>.</li>
<li>pytest-profiling: Removed usage of <code>distutils</code>, where possible.</li>
<li>pytest-server-fixtures: Correct httpd command line</li>
<li>pytest-server-fixtures: Minor bugfix now that workspace.workspace is a Path object.</li>
<li>pytest-virtualenv: Added default to install editable packages by using direct_url.json, if it exists</li>
<li>pytest-virtualenv: Fixed Windows compatibility issues</li>
<li>ci: Remove custom hooks from <code>python setup.py test</code> since this is no longer supported.</li>
<li>ci: Fix build-related buttons in README.md.</li>
</ul>
<h2>v1.8.0</h2>
<ul>
<li>All: Drop support for Python 2 and &lt;3.6, removing compatibility code.</li>
<li>All: Use stdlib unittest.mock instead of mock package.</li>
<li>All: Removed usage of path.py and path in favour of pathlib. <a href="">#174</a> <a href="">#224</a></li>
<li>pytest-devpi-server: Run devpi-init for initialisation. <a href="">#179</a></li>
<li>pytest-server-fixtures: BREAKING CHANGE: Removed RethinkDB support, as the mirror was no longer available.</li>
<li>pytest-server-fixtures: Allowed passing through HTTP headers to the server. <a href="">#149</a></li>
<li>pytest-server-fixtures: Fixed threading log debug messages. <a href="">#146</a></li>
<li>pytest-server-fixtures: Removed usage of deprecated Thread.setDaemon. <a href="">#202</a></li>
<li>pytest-server-fixtures: Explicitly close initial Mongo client. <a href="">#198</a></li>
<li>pytest-server-fixtures: Don't use context manager for CREATE DATABASE <a href="">#186</a></li>
<li>pytest-shutil: Removed contextlib2 requirement. <a href="">#144</a></li>
<li>pytest-shutil: Fixed forcing color through termcolor. <a href="">#217</a></li>
<li>pytest-shutil: Replaced deprecated imp module <a href="">#219</a></li>
<li>pytest-profiling: Added support to hide/show the full path of file. <a href="">#95</a></li>
<li>pytest-profiling: Fixed SVG file generation on Windows. <a href="">#93</a></li>
<li>pytest-profiling: Remove pinning of more-itertools. <a href="">#194</a></li>
<li>pytest-profiling: Add support to define element number for print_stats() <a href="">#96</a></li>
<li>pytest-profiling: Fix mock in test_writes_summary <a href="">#223</a></li>
<li>pytest-virtualenv: Modernised package. <a href="">#188</a> <a href="">#185</a> <a href="">#182</a> <a href="">#163</a></li>
<li>pytest-virtualenv: Fixed virtualenv creation on Windows. <a href="">#142</a></li>
<li>pytest-virtualenv: Added delete_workspace parameter to VirtualEnv. <a href="">#195</a></li>
<li>pytest-virtualenv: Removed extras_require. <a href="">#240</a></li>
<li>ci: Remove usage of deprecated distutils. <a href="">#189</a></li>
<li>ci: Disabled jenkins server tests on CircleCI to improve build time.</li>
<li>ci: Fixed <code>collections</code> import for py 3.11 compatibility <a href="">#222</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/man-group/pytest-plugins/blob/master/CHANGES.md">pytest-profiling's changelog</a>.</em></p>
<blockquote>
<h3>1.8.1 (2024-11-29)</h3>
<ul>
<li>All: Add a CircleCI Windows build with py3.6-py3.12 and remove references to TravisCI. (<a href="">#246</a>)</li>
<li>All: Add Ubuntu builds for py3.6-3.13</li>
<li>All: CircleCI release jobs now depend on both Ubuntu and Windows success.</li>
<li>pytest-listener: Use py_modules in setup.py</li>
<li>pytest-listener: Fix flakiness on py3.9+ on Windows when the receive time was equal to the clear_time.</li>
<li>pytest-profiling: Small refactor to make error messages a bit clearer</li>
<li>pytest-profiling: Fixed tests which were installing from PyPI rather than local</li>
<li>pytest-profiling: Removed usage of deprecated <code>pytest.yield_fixture</code>.</li>
<li>pytest-profiling: Removed usage of <code>distutils</code>, where possible.</li>
<li>pytest-server-fixtures: Correct httpd command line</li>
<li>pytest-server-fixtures: Minor bugfix now that workspace.workspace is a Path object.</li>
<li>pytest-virtualenv: Added default to install editable packages by using direct_url.json, if it exists</li>
<li>pytest-virtualenv: Fixed Windows compatibility issues</li>
<li>ci: Remove custom hooks from <code>python setup.py test</code> since this is no longer supported.</li>
<li>ci: Fix build-related buttons in README.md.</li>
</ul>
<h3>1.8.0 (2024-10-17)</h3>
<ul>
<li>All: Drop support for Python 2 and &lt;3.6, removing compatibility code.</li>
<li>All: Use stdlib unittest.mock instead of mock package.</li>
<li>All: Removed usage of path.py and path in favour of pathlib. <a href="">#174</a> <a href="">#224</a></li>
<li>pytest-devpi-server: Run devpi-init for initialisation. <a href="">#179</a></li>
<li>pytest-server-fixtures: BREAKING CHANGE: Removed RethinkDB support, as the project is no longer maintained.</li>
<li>pytest-server-fixtures: Allowed passing through HTTP headers to the server. <a href="">#149</a></li>
<li>pytest-server-fixtures: Fixed threading log debug messages. <a href="">#146</a></li>
<li>pytest-server-fixtures: Removed usage of deprecated Thread.setDaemon. <a href="">#202</a></li>
<li>pytest-server-fixtures: Explicitly close initial Mongo client. <a href="">#198</a></li>
<li>pytest-server-fixtures: Don't use context manager for CREATE DATABASE <a href="">#186</a></li>
<li>pytest-shutil: Removed contextlib2 requirement. <a href="">#144</a></li>
<li>pytest-shutil: Fixed forcing color through termcolor. <a href="">#217</a></li>
<li>pytest-shutil: Replaced deprecated imp module <a href="">#219</a></li>
<li>pytest-profiling: Added support to hide/show the full path of file. <a href="">#95</a></li>
<li>pytest-profiling: Fixed SVG file generation on Windows. <a href="">#93</a></li>
<li>pytest-profiling: Remove pinning of more-itertools. <a href="">#194</a></li>
<li>pytest-profiling: Add support to define element number for print_stats() <a href="">#96</a></li>
<li>pytest-profiling: Fix mock in test_writes_summary <a href="">#223</a></li>
<li>pytest-virtualenv: Modernised package. <a href="">#188</a> <a href="">#185</a> <a href="">#182</a> <a href="">#163</a></li>
<li>pytest-virtualenv: Fixed virtualenv creation on Windows. <a href="">#142</a></li>
<li>pytest-virtualenv: Added delete_workspace parameter to VirtualEnv. <a href="">#195</a></li>
<li>pytest-virtualenv: Removed extras_require. <a href="">#240</a></li>
<li>ci: Remove usage of deprecated distutils. <a href="">#189</a></li>
<li>ci: Disabled jenkins server tests on CircleCI to improve build time.</li>
<li>ci: Fixed <code>collections</code> import for py 3.11 compatibility <a href="">#222</a></li>
</ul>
<h3>1.7.1 (2019-05-28)</h3>
<ul>
<li>pytest-profiling: Fix pytest-profiling to profile fixtures. <a href="">#48</a></li>
<li>pytest-devpi-server: Fixed Python 3.4 support updating &quot;ruamel.yaml&quot; requirements. <a href="">#138</a></li>
<li>ci: Added  PYTEST_DONT_REWRITE in order to suppress module already imported. <a href="">#123</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ce6b157</code></a> Release version 1.8.1</li>
<li><a href=""><code>879f929</code></a> pytest-listener: Fix flakiness on windows-py39+ due to receive() happening on...</li>
<li><a href=""><code>5480ab9</code></a> pytest-listener: Use py_modules in setup.py</li>
<li><a href=""><code>37cea8d</code></a> pytest-server-fixtures: Correct httpd command line</li>
<li><a href=""><code>21aa8c5</code></a> Add builds for new py versions and Windows to CircleCI (<a href="">#245</a>)</li>
<li><a href=""><code>286e040</code></a> Release 1.8.0  (<a href="">#241</a>)</li>
<li><a href=""><code>01b3fb2</code></a> Merge pull request <a href="">#226</a> from man-group/224-fix-shutil</li>
<li><a href=""><code>1a74776</code></a> Remove outdated requirements, and fix another test</li>
<li><a href=""><code>c16e075</code></a> Fix a few more tests</li>
<li><a href=""><code>ebf746f</code></a> Fix tests</li>
<li>Additional commits viewable in <a href="https://github.com/man-group/pytest-plugins/compare/v1.7.0...v1.8.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest-profiling&package-manager=pip&previous-version=1.7.0&new-version=1.8.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump pytest-profiling from version 1.7.0 to 1.8.1 in the development dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fcc6ea391a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.