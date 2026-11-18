# Issue

**Title:** Bump numpy from 1.18.4 to 1.18.5

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.18.4 to 1.18.5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/numpy/numpy/releases">numpy's releases</a>.</em></p>
<blockquote>
<h2>v1.18.5</h2>
<h1>NumPy 1.18.5 Release Notes</h1>
<p>This is a short release to allow pickle <code>protocol=5</code> to be used in
Python3.5. It is motivated by the recent backport of pickle5 to
Python3.5.</p>
<p>The Python versions supported in this release are 3.5-3.8. Downstream
developers should use Cython &gt;= 0.29.15 for Python 3.8 support and
OpenBLAS &gt;= 3.7 to avoid errors on the Skylake architecture.</p>
<h2>Contributors</h2>
<p>A total of 3 people contributed to this release. People with a &quot;+&quot; by
their names contributed a patch for the first time.</p>
<ul>
<li>Charles Harris</li>
<li>Matti Picus</li>
<li>Siyuan Zhuang +</li>
</ul>
<h2>Pull requests merged</h2>
<p>A total of 2 pull requests were merged for this release.</p>
<ul>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/16439">#16439</a>: ENH: enable pickle protocol 5 support for python3.5</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/pull/16441">#16441</a>: BUG: relpath fails for different drives on windows</li>
</ul>
<h2>Checksums</h2>
<h3>MD5</h3>
<pre><code>f923519347ba9f6bca59dce0583bdbd5  numpy-1.18.5-cp35-cp35m-macosx_10_9_intel.whl
79990253bda9ffa2db75152e77c318e9  numpy-1.18.5-cp35-cp35m-manylinux1_i686.whl
d5bf77d6caf4f83ed871ab9e4f9d1f72  numpy-1.18.5-cp35-cp35m-manylinux1_x86_64.whl
2cc7cc1b1640d6b50c50d96a35624698  numpy-1.18.5-cp35-cp35m-win32.whl
5a93e72e30c56462492a29315e19c0cc  numpy-1.18.5-cp35-cp35m-win_amd64.whl
caef5b4785e5deb6891f118a49d48ccc  numpy-1.18.5-cp36-cp36m-macosx_10_9_x86_64.whl
402be8c771c2541c7ee936ef63c9ebc0  numpy-1.18.5-cp36-cp36m-manylinux1_i686.whl
259dbb8694209921d56ffb091ae42b5b  numpy-1.18.5-cp36-cp36m-manylinux1_x86_64.whl
9188a301a9640836322f2dc926640515  numpy-1.18.5-cp36-cp36m-win32.whl
acfa82d4e66601386dad19ad3a3983a5  numpy-1.18.5-cp36-cp36m-win_amd64.whl
bc1ebaa1ecf20f22b72cbb824c9cbc21  numpy-1.18.5-cp37-cp37m-macosx_10_9_x86_64.whl
97f27a6e2e6951cf8107132e7c628004  numpy-1.18.5-cp37-cp37m-manylinux1_i686.whl
f261237ab3d47b9b6e859bf240014a48  numpy-1.18.5-cp37-cp37m-manylinux1_x86_64.whl
08bdf2289600c5c728a2668b585fdd02  numpy-1.18.5-cp37-cp37m-win32.whl
8b793d97dae258d06e63c452a2684b16  numpy-1.18.5-cp37-cp37m-win_amd64.whl
</code></pre>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>32f514f</code></a> REL: NumPy 1.18.5 release.</li>
<li><a href=""><code>690cf54</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16486">#16486</a> from charris/prepare-1.18.5-release</li>
<li><a href=""><code>683ea7b</code></a> REL: Prepare for NumPy 1.18.5 release.</li>
<li><a href=""><code>9939902</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16439">#16439</a> from suquark/pickle5_py35</li>
<li><a href=""><code>5287663</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16441">#16441</a> from charris/backport-16308</li>
<li><a href=""><code>48b04f1</code></a> BUG: relpath fails for different drives on windows (<a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16308">#16308</a>)</li>
<li><a href=""><code>b8bdf30</code></a> update test requirements</li>
<li><a href=""><code>9d3f221</code></a> update tests related to pickle5</li>
<li><a href=""><code>17aecae</code></a> ENH: enable pickle protocol 5 support for python3.5</li>
<li><a href=""><code>5c41082</code></a> REL: prepare 1.18.x for further development</li>
<li>See full diff in <a href="https://github.com/numpy/numpy/compare/v1.18.4...v1.18.5">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.18.4&new-version=1.18.5)](https://dependabot.com/compatibility-score/?dependency-name=numpy&package-manager=pip&previous-version=1.18.4&new-version=1.18.5)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb956798c56a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.