# Issue

**Title:** Bump scipy from 1.4.1 to 1.5.0

## Description

Bumps [scipy](https://github.com/scipy/scipy) from 1.4.1 to 1.5.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/scipy/scipy/releases">scipy's releases</a>.</em></p>
<blockquote>
<h1>SciPy 1.5.0 Release Notes</h1>
<p>SciPy <code>1.5.0</code> is the culmination of 6 months of hard work. It contains
many new features, numerous bug-fixes, improved test coverage and better
documentation. There have been a number of deprecations and API changes
in this release, which are documented below. All users are encouraged to
upgrade to this release, as there are a large number of bug-fixes and
optimizations. Before upgrading, we recommend that users check that
their own code does not use deprecated SciPy functionality (to do so,
run your code with <code>python -Wd</code> and check for <code>DeprecationWarning</code> s).
Our development attention will now shift to bug-fix releases on the
1.5.x branch, and on adding new features on the master branch.</p>
<p>This release requires Python <code>3.6+</code> and NumPy <code>1.14.5</code> or greater.</p>
<p>For running on PyPy, PyPy3 <code>6.0+</code> and NumPy <code>1.15.0</code> are required.</p>
<h2>Highlights of this release</h2>
<ul>
<li>wrappers for more than a dozen new <code>LAPACK</code> routines are now available
in <code>scipy.linalg.lapack</code></li>
<li>Improved support for leveraging 64-bit integer size from linear algebra
backends</li>
<li>addition of the probability distribution for two-sided one-sample
Kolmogorov-Smirnov tests</li>
</ul>
<h2>New features</h2>
<h2><code>scipy.cluster</code> improvements</h2>
<p>Initialization of <code>scipy.cluster.vq.kmeans2</code> using <code>minit=&quot;++&quot;</code> had a
quadratic complexity in the number of samples. It has been improved, resulting
in a much faster initialization with quasi-linear complexity.</p>
<p><code>scipy.cluster.hierarchy.dendrogram</code> now respects the <code>matplotlib</code> color
palette</p>
<h2><code>scipy.fft</code> improvements</h2>
<p>A new keyword-only argument <code>plan</code> is added to all FFT functions in this
module. It is reserved for passing in a precomputed plan from libraries
providing a FFT backend (such as <code>PyFFTW</code> and <code>mkl-fft</code>), and it is
currently not used in SciPy.</p>
<h2><code>scipy.integrate</code> improvements</h2>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>4c0fd79</code></a> REL: set version to 1.5.0 &quot;final&quot;</li>
<li><a href=""><code>ce8c972</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/scipy/scipy/issues/12391">#12391</a> from tylerjereddy/prep_scipy_150_final</li>
<li><a href=""><code>d60c1b3</code></a> MAINT: prepare for SciPy 1.5.0 &quot;final&quot;</li>
<li><a href=""><code>a7131fa</code></a> REL: set version to 1.5.0rc2 released</li>
<li><a href=""><code>896480b</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/scipy/scipy/issues/12345">#12345</a> from tylerjereddy/treddy_150rc2_backports</li>
<li><a href=""><code>1e5c8d9</code></a> DOC: 1.5.0rc2 release notes update</li>
<li><a href=""><code>e468042</code></a> CI: don't install pydata/sparse when running on Numpy prerelease</li>
<li><a href=""><code>3d96899</code></a> CI: split travis arm64 run into two</li>
<li><a href=""><code>a3795e9</code></a> DOC: update SciPy 1.5.0rc2 release notes</li>
<li><a href=""><code>9803615</code></a> MAINT: Work around Sphinx bug (<a href="https://github-redirect.dependabot.com/scipy/scipy/issues/12335">#12335</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/scipy/scipy/compare/v1.4.1...v1.5.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=scipy&package-manager=pip&previous-version=1.4.1&new-version=1.5.0)](https://dependabot.com/compatibility-score/?dependency-name=scipy&package-manager=pip&previous-version=1.4.1&new-version=1.5.0)

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