# Issue

**Title:** Bump scipy from 1.3.1 to 1.4.1

## Description

Bumps [scipy](https://github.com/scipy/scipy) from 1.3.1 to 1.4.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/scipy/scipy/releases">scipy's releases</a>.</em></p>
<blockquote>
<h1>SciPy 1.4.1 Release Notes</h1>
<p>SciPy <code>1.4.1</code> is a bug-fix release with no new features
compared to <code>1.4.0</code>. Importantly, it aims to fix a problem
where an older version of <code>pybind11</code> may cause a segmentation
fault when imported alongside incompatible libraries.</p>
<h1>Authors</h1>
<ul>
<li>Ralf Gommers</li>
<li>Tyler Reddy</li>
</ul>
<h1>SciPy 1.4.0 Release Notes</h1>
<p>SciPy <code>1.4.0</code> is the culmination of 6 months of hard work. It contains
many new features, numerous bug-fixes, improved test coverage and better
documentation. There have been a number of deprecations and API changes
in this release, which are documented below. All users are encouraged to
upgrade to this release, as there are a large number of bug-fixes and
optimizations. Before upgrading, we recommend that users check that
their own code does not use deprecated SciPy functionality (to do so,
run your code with <code>python -Wd</code> and check for <code>DeprecationWarning</code> s).
Our development attention will now shift to bug-fix releases on the
1.4.x branch, and on adding new features on the master branch.</p>
<p>This release requires Python <code>3.5+</code> and NumPy <code>&gt;=1.13.3</code> (for Python <code>3.5</code>, <code>3.6</code>),
<code>&gt;=1.14.5</code> (for Python <code>3.7</code>), <code>&gt;= 1.17.3</code> (for Python <code>3.8</code>)</p>
<p>For running on PyPy, PyPy3 <code>6.0+</code> and NumPy <code>1.15.0</code> are required.</p>
<h2>Highlights of this release</h2>
<ul>
<li>a new submodule, <code>scipy.fft</code>, now supersedes <code>scipy.fftpack</code>; this
means support for <code>long double</code> transforms, faster multi-dimensional
transforms, improved algorithm time complexity, release of the global
intepreter lock, and control over threading behavior</li>
<li>support for <code>pydata/sparse</code> arrays in <code>scipy.sparse.linalg</code></li>
<li>substantial improvement to the documentation and functionality of
several <code>scipy.special</code> functions, and some new additions</li>
<li>the generalized inverse Gaussian distribution has been added to
<code>scipy.stats</code></li>
<li>an implementation of the Edmonds-Karp algorithm in
<code>scipy.sparse.csgraph.maximum_flow</code></li>
<li><code>scipy.spatial.SphericalVoronoi</code> now supports n-dimensional input,
has linear memory complexity, improved performance, and
supports single-hemisphere generators</li>
</ul>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>adc4f4f</code></a> REL: SciPy 1.4.1 release commit</li>
<li><a href=""><code>470c16d</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/scipy/scipy/issues/11240">#11240</a> from tylerjereddy/treddy_prep_141</li>
<li><a href=""><code>87b5c30</code></a> DOC: 1.4.1 release notes revision</li>
<li><a href=""><code>29bf2cd</code></a> BLD: update minimum pybind11 version to 2.4.0.</li>
<li><a href=""><code>d45fb7e</code></a> MAINT, REL: prepare for SciPy 1.4.1</li>
<li><a href=""><code>f533e91</code></a> REL: set version to 1.4.0</li>
<li><a href=""><code>2d85bb2</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/scipy/scipy/issues/11221">#11221</a> from tylerjereddy/scipy-140-rel-prep</li>
<li><a href=""><code>c705210</code></a> DOC: update 1.4.0 release notes</li>
<li><a href=""><code>be5fe99</code></a> BUG: sparse.linalg: mistake in unsymm. real shift-invert ARPACK eigenvalue se...</li>
<li><a href=""><code>119bf01</code></a> TST: Bump up tolerance for test_maxiter_worsening</li>
<li>Additional commits viewable in <a href="https://github.com/scipy/scipy/compare/v1.3.1...v1.4.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=scipy&package-manager=pip&previous-version=1.3.1&new-version=1.4.1)](https://dependabot.com/compatibility-score.html?dependency-name=scipy&package-manager=pip&previous-version=1.3.1&new-version=1.4.1)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `681ee9625efa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.