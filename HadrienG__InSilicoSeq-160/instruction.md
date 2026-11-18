# Issue

**Title:** Bump numpy from 1.18.3 to 1.18.4

## Description

Bumps [numpy](https://github.com/numpy/numpy) from 1.18.3 to 1.18.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/numpy/numpy/releases">numpy's releases</a>.</em></p>
<blockquote>
<h2>v1.18.4</h2>
<hr />
<h2>title: 'NumPy 1.18.4 Release Notes'</h2>
<p>This is that last planned release in the 1.18.x series. It reverts the
<code>bool(&quot;0&quot;)</code> behavior introduced in 1.18.3 and fixes a bug in
<code>Generator.integers</code>. There is also improved help in the error message
emitted when numpy import fails due to a link to a new troubleshooting
section in the documentation that is now included.</p>
<p>The Python versions supported in this release are 3.5-3.8. Downstream
developers should use Cython &gt;= 0.29.15 for Python 3.8 support and
OpenBLAS &gt;= 3.7 to avoid errors on the Skylake architecture.</p>
<h1>Contributors</h1>
<p>A total of 4 people contributed to this release. People with a &quot;+&quot; by
their names contributed a patch for the first time.</p>
<ul>
<li>Charles Harris</li>
<li>Matti Picus</li>
<li>Sebastian Berg</li>
<li>Warren Weckesser</li>
</ul>
<h1>Pull requests merged</h1>
<p>A total of 6 pull requests were merged for this release.</p>
<ul>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16055">#16055</a> BLD: add i686 for 1.18 builds</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16090">#16090</a> BUG: random: <code>Generator.integers(2**32)</code> always returned 0.</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16091">#16091</a> BLD: fix path to libgfortran on macOS</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16109">#16109</a> REV: Reverts side-effect changes to casting</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16114">#16114</a> BLD: put openblas library in local directory on windows</li>
<li><a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16132">#16132</a> DOC: Change import error &quot;howto&quot; to link to new troubleshooting...</li>
</ul>
<h1>Checksums</h1>
<h2>MD5</h2>
<pre><code>1fe09153c9e6da5c9e73f3ed466da50c  numpy-1.18.4-cp35-cp35m-macosx_10_9_intel.whl
707b0270ece3e9a16905e756884daa48  numpy-1.18.4-cp35-cp35m-manylinux1_i686.whl
47f90c71c3df80ace2b32d011ed1c240  numpy-1.18.4-cp35-cp35m-manylinux1_x86_64.whl
e0e7d9fd9f4c8cf077ba5cda69833d38  numpy-1.18.4-cp35-cp35m-win32.whl
06e844091463932a0d4da103951ffc2c  numpy-1.18.4-cp35-cp35m-win_amd64.whl
32ce3d6d266f1fbfef4a2ff917053718  numpy-1.18.4-cp36-cp36m-macosx_10_9_x86_64.whl
</code></pre>
</tr></table> ... (truncated)
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>9472132</code></a> REL: NumPy 1.18.4 release.</li>
<li><a href=""><code>40bb731</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16140">#16140</a> from charris/prepare-1.18.4-release</li>
<li><a href=""><code>b96c124</code></a> REL: Prepare for the NumPy 1.18.4 release.</li>
<li><a href=""><code>e8ace4a</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16132">#16132</a> from charris/backport-16014</li>
<li><a href=""><code>c369fab</code></a> Fix other comments from Ross and make it ImportError specific</li>
<li><a href=""><code>c65fbd2</code></a> Apply suggestions from code review</li>
<li><a href=""><code>8131c2e</code></a> DOC: Change import error &quot;howto&quot; to link to troubleshooting docs</li>
<li><a href=""><code>6586541</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16109">#16109</a> from seberg/revert-accidental-bool-fix</li>
<li><a href=""><code>373fb29</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16114">#16114</a> from charris/backport-16101</li>
<li><a href=""><code>f591381</code></a> BLD: put openblas library in local directory on windows (<a href="https://github-redirect.dependabot.com/numpy/numpy/issues/16101">#16101</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/numpy/numpy/compare/v1.18.3...v1.18.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=numpy&package-manager=pip&previous-version=1.18.3&new-version=1.18.4)](https://dependabot.com/compatibility-score/?dependency-name=numpy&package-manager=pip&previous-version=1.18.3&new-version=1.18.4)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f0f3fe2abd97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.