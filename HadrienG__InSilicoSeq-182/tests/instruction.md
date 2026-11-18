# Issue

**Title:** Bump numpy from 1.18.5 to 1.19.0

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.18.5 to 1.19.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/numpy/numpy/releases">numpy's releases</a>.</em></p>
<blockquote>
<h2>v1.19.0</h2>
<h1>NumPy 1.19.0 Release Notes</h1>
<p>This NumPy release is marked by the removal of much technical debt:
support for Python 2 has been removed, many deprecations have been
expired, and documentation has been improved. The polishing of the
random module continues apace with bug fixes and better usability from
Cython.</p>
<p>The Python versions supported for this release are 3.6-3.8. Downstream
developers should use Cython &gt;= 0.29.16 for Python 3.8 support and
OpenBLAS &gt;= 3.7 to avoid problems on the Skylake architecture.</p>
<h2>Highlights</h2>
<ul>
<li>
<p>Code compatibility with Python versions &lt; 3.6 (including Python 2)
was dropped from both the python and C code. The shims in
<code>numpy.compat</code> will remain to support third-party packages, but they
may be deprecated in a future release. Note that 1.19.x will <em>not</em>
compile with earlier versions of Python due to the use of f-strings.</p>
<p>(<a href="https://github-redirect.dependabot.com/numpy/numpy/pull/15233">gh-15233</a>)</p>
</li>
</ul>
<h2>Expired deprecations</h2>
<h3><code>numpy.insert</code> and <code>numpy.delete</code> can no longer be passed an axis on 0d arrays</h3>
<p>This concludes a deprecation from 1.9, where when an <code>axis</code> argument was
passed to a call to <code>~numpy.insert</code> and <code>~numpy.delete</code> on a 0d array,
the <code>axis</code> and <code>obj</code> argument and indices would be completely ignored.
In these cases, <code>insert(arr, &quot;nonsense&quot;, 42, axis=0)</code> would actually
overwrite the entire array, while <code>delete(arr, &quot;nonsense&quot;, axis=0)</code>
would be <code>arr.copy()</code></p>
<p>Now passing <code>axis</code> on a 0d array raises <code>~numpy.AxisError</code>.</p>
<p>(<a href="https://github-redirect.dependabot.com/numpy/numpy/pull/15802">gh-15802</a>)</p>
<h3><code>numpy.delete</code> no longer ignores out-of-bounds indices</h3>
<p>This concludes deprecations from 1.8 and 1.9, where <code>np.delete</code> would
ignore both negative and out-of-bounds items in a sequence of indices.
This was at odds with its behavior when passed a single index.</p>
<p>Now out-of-bounds items throw <code>IndexError</code>, and negative items index
from the end.</p>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/numpy/numpy/blob/master/doc/HOWTO_RELEASE.rst.txt">numpy's changelog</a>.</em></p>
<blockquote>
<p>This file gives an overview of what is necessary to build binary releases for
NumPy.</p>
<h1>Current build and release info</h1>
<p>The current info on building and releasing NumPy and SciPy is scattered in
several places. It should be summarized in one place, updated, and where
necessary described in more detail. The sections below list all places where
useful info can be found.</p>
<h2>Source tree</h2>
<ul>
<li>INSTALL.rst.txt</li>
<li>release.sh</li>
<li>pavement.py</li>
</ul>
<h2>NumPy Docs</h2>
<ul>
<li><a href="https://github.com/numpy/numpy/blob/master/doc/HOWTO_RELEASE.rst.txt">https://github.com/numpy/numpy/blob/master/doc/HOWTO_RELEASE.rst.txt</a></li>
</ul>
<h2>SciPy.org wiki</h2>
<ul>
<li><a href="https://www.scipy.org/Installing_SciPy">https://www.scipy.org/Installing_SciPy</a> and links on that page.</li>
</ul>
<h2>Release Scripts</h2>
<ul>
<li><a href="https://github.com/numpy/numpy-vendor">https://github.com/numpy/numpy-vendor</a></li>
</ul>
<h1>Supported platforms and versions</h1>
<p>:ref:<code>NEP 29 &lt;NEP29&gt;</code> outlines which Python versions
are supported; For the first half of 2020, this will be Python &gt;= 3.6. We test
NumPy against all these versions every time we merge code to master.  Binary
installers may be available for a subset of these versions (see below).</p>
<h2>OS X</h2>
<p>OS X versions &gt;= 10.9 are supported, for Python version support see
:ref:<code>NEP 29 &lt;NEP29&gt;</code>. We build binary wheels for
OSX that are compatible with Python.org Python, system Python, homebrew and
macports - see this <code>OSX wheel building summary &lt;https://github.com/MacPython/wiki/wiki/Spinning-wheels&gt;</code>_ for details.</p>
<p>Windows</p>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>92ebe1e</code></a> REL: NumPy 1.14.5 release.</li>
<li><a href=""><code>8f364cd</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16645">#16645</a> from charris/prepare-1.19.0-release</li>
<li><a href=""><code>7a06267</code></a> DOC: Update 1.19.0-changelog.rst for 1.19.0 release.</li>
<li><a href=""><code>516d70d</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16602">#16602</a> from charris/test_ignore_nan_ulperror</li>
<li><a href=""><code>8ecbf34</code></a> MAINT: Move and improve test_ignore_nan_ulperror.</li>
<li><a href=""><code>c17b6fa</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16586">#16586</a> from charris/backport-16572</li>
<li><a href=""><code>a1e166a</code></a> Add test for sin/cos for strided large inputs</li>
<li><a href=""><code>d90f20f</code></a> BUG: fix sin/cos bug when input is strided</li>
<li><a href=""><code>d167bb7</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16563">#16563</a> from charris/backport-16551</li>
<li><a href=""><code>a9a7993</code></a> DOC: Add release note.</li>
<li>Additional commits viewable in <a href="https://github.com/numpy/numpy/compare/v1.18.5...v1.19.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.18.5&new-version=1.19.0)](https://dependabot.com/compatibility-score/?dependency-name=numpy&package-manager=pip&previous-version=1.18.5&new-version=1.19.0)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Pull request limits (per update run and/or open at any time)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3dc1a0cf1b24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.