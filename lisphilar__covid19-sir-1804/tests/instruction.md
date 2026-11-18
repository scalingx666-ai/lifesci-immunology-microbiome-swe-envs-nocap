# Issue

**Title:** build(deps-dev): bump pytest from 8.3.4 to 8.3.5

## Description

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.3.4 to 8.3.5.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.3.5</h2>
<h1>pytest 8.3.5 (2025-03-02)</h1>
<h2>Bug fixes</h2>
<ul>
<li><a href="">#11777</a>: Fixed issue where sequences were still being shortened even with <code>-vv</code> verbosity.</li>
<li><a href="">#12888</a>: Fixed broken input when using Python 3.13+ and a <code>libedit</code> build of Python, such as on macOS or with uv-managed Python binaries from the <code>python-build-standalone</code> project. This could manifest e.g. by a broken prompt when using <code>Pdb</code>, or seeing empty inputs with manual usage of <code>input()</code> and suspended capturing.</li>
<li><a href="">#13026</a>: Fixed <code>AttributeError</code>{.interpreted-text role=&quot;class&quot;} crash when using <code>--import-mode=importlib</code> when top-level directory same name as another module of the standard library.</li>
<li><a href="">#13053</a>: Fixed a regression in pytest 8.3.4 where, when using <code>--import-mode=importlib</code>, a directory containing py file with the same name would cause an <code>ImportError</code></li>
<li><a href="">#13083</a>: Fixed issue where pytest could crash if one of the collected directories got removed during collection.</li>
</ul>
<h2>Improved documentation</h2>
<ul>
<li>
<p><a href="">#12842</a>: Added dedicated page about using types with pytest.</p>
<p>See <code>types</code>{.interpreted-text role=&quot;ref&quot;} for detailed usage.</p>
</li>
</ul>
<h2>Contributor-facing changes</h2>
<ul>
<li><a href="">#13112</a>: Fixed selftest failures in <code>test_terminal.py</code> with Pygments &gt;= 2.19.0</li>
<li><a href="">#13256</a>: Support for Towncrier versions released in 2024 has been re-enabled
when building Sphinx docs -- by <code>webknjaz</code>{.interpreted-text role=&quot;user&quot;}.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>b55ab2a</code></a> Prepare release version 8.3.5</li>
<li><a href=""><code>e217726</code></a> Added dedicated page about using types with pytest <a href="">#12842</a> (<a href="">#12963</a>) (<a href="">#13260</a>)</li>
<li><a href=""><code>2fa3f83</code></a> Add more resources and studies to flaky tests page in docs (<a href="">#13250</a>) (<a href="">#13259</a>)</li>
<li><a href=""><code>e5c2efe</code></a> Merge pull request <a href="">#13256</a> from webknjaz/maintenance/towncrier-bump (<a href="">#13258</a>)</li>
<li><a href=""><code>3419674</code></a> Merge pull request <a href="">#13187</a> from pytest-dev/patchback/backports/8.3.x/b4009b319...</li>
<li><a href=""><code>b75cfb1</code></a> Add readline workaround for libedit (<a href="">#13176</a>)</li>
<li><a href=""><code>edbfff7</code></a> doc: Clarify capturing .readouterr() return value (<a href="">#13222</a>) (<a href="">#13225</a>)</li>
<li><a href=""><code>2ebba00</code></a> Merge pull request <a href="">#13199</a> from jakkdl/tox_docs_no_fetch (<a href="">#13200</a>)</li>
<li><a href=""><code>eb6496b</code></a> doc: Change training to remote only (<a href="">#13196</a>) (<a href="">#13197</a>)</li>
<li><a href=""><code>78cf1f6</code></a> ci: Bump build-and-inspect-python-package (<a href="">#13188</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.3.4...8.3.5">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.3.4&new-version=8.3.5)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Update pytest dependency from 8.3.4 to 8.3.5.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfaaa7f37eef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.