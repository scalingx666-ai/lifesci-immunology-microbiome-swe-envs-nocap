# Issue

**Title:** Bump numpy from 1.17.4 to 1.18.3

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.17.4 to 1.18.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/numpy/numpy/releases">numpy's releases</a>.</em></p>
<blockquote>
<h2>v1.18.3</h2>
<h1>NumPy 1.18.3 Release Notes</h1>
<p>This release contains various bug/regression fixes.</p>
<p>The Python versions supported in this release are 3.5-3.8. Downstream
developers should use Cython &gt;= 0.29.15 for Python 3.8 support and
OpenBLAS &gt;= 3.7 to avoid errors on the Skylake architecture.</p>
<h2>Highlights</h2>
<ul>
<li>Fix for the <code>method='eigh'</code> and <code>method='cholesky'</code> options in
<code>numpy.random.multivariate_normal</code>. Those were producing samples
from the wrong distribution.</li>
</ul>
<h2>Contributors</h2>
<p>A total of 6 people contributed to this release. People with a &quot;+&quot; by
their names contributed a patch for the first time.</p>
<ul>
<li>Charles Harris</li>
<li>Max Balandat +</li>
<li><a href="https://github.com/Mibu287">@Mibu287</a> +</li>
<li>Pan Jan +</li>
<li>Sebastian Berg</li>
<li><a href="https://github.com/panpiort8">@panpiort8</a> +</li>
</ul>
<h2>Pull requests merged</h2>
<p>A total of 5 pull requests were merged for this release.</p>
<ul>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/15916">#15916</a>: BUG: Fix eigh and cholesky methods of numpy.random.multivariate_normal</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/15929">#15929</a>: BUG,MAINT: Remove incorrect special case in string to number...</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/15930">#15930</a>: BUG: Guarantee array is in valid state after memory error occurs...</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/15954">#15954</a>: BUG: Check that [pvals]{.title-ref} is 1D in <code>_generator.multinomial</code>.</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/16017">#16017</a>: BUG: Alpha parameter must be 1D in <code>_generator.dirichlet</code></li>
</ul>
<h2>Checksums</h2>
<h3>MD5</h3>
<pre><code>6582c9a045ba92cb11a7062cfabba898  numpy-1.18.3-cp35-cp35m-macosx_10_9_intel.whl
f70d5c8d4f598653ff66f640487481ce  numpy-1.18.3-cp35-cp35m-manylinux1_i686.whl
5c0f1a8c94d095efd21ab4b8ffeed921  numpy-1.18.3-cp35-cp35m-manylinux1_x86_64.whl
92cab35405fe3042e7aa8504d8669cd0  numpy-1.18.3-cp35-cp35m-win32.whl
</code></pre>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b07baa1</code></a> REL: NumPy 1.18.3 release.</li>
<li><a href=""><code>69a3f66</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16020">#16020</a> from charris/prepare-1.18.3</li>
<li><a href=""><code>31eac51</code></a> REL: Prepare for NumPy 1.18.3 release.</li>
<li><a href=""><code>c0b6896</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16017">#16017</a> from charris/backport-15951</li>
<li><a href=""><code>b17be04</code></a> BUG: Alpha parameter must be 1D in <code>generator.dirichlet</code> (<a href="https://github-redirect.dependabot.com/numpy/numpy/issues/15951">#15951</a>)</li>
<li><a href=""><code>6530310</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/15954">#15954</a> from charris/backport-15876</li>
<li><a href=""><code>bd55a55</code></a> Add minor tests enhancement</li>
<li><a href=""><code>80844b9</code></a> Replace checks with direct function call</li>
<li><a href=""><code>a752bf4</code></a> Add testing and replace check</li>
<li><a href=""><code>8bb77f8</code></a> BUG: add check if pvals is 1d array in numpy.random.*.multinomial</li>
<li>Additional commits viewable in <a href="https://github.com/numpy/numpy/compare/v1.17.4...v1.18.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.17.4&new-version=1.18.3)](https://dependabot.com/compatibility-score/?dependency-name=numpy&package-manager=pip&previous-version=1.17.4&new-version=1.18.3)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee50843aa9d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.