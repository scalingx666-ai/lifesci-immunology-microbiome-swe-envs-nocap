# Issue

**Title:** build(deps-dev): bump pytest from 8.3.2 to 8.3.3

## Description

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.3.2 to 8.3.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.3.3</h2>
<h1>pytest 8.3.3 (2024-09-09)</h1>
<h2>Bug fixes</h2>
<ul>
<li>
<p><a href="">#12446</a>: Avoid calling <code>@property</code> (and other instance descriptors) during fixture discovery -- by <code>asottile</code>{.interpreted-text role=&quot;user&quot;}</p>
</li>
<li>
<p><a href="">#12659</a>: Fixed the issue of not displaying assertion failure differences when using the parameter <code>--import-mode=importlib</code> in pytest&gt;=8.1.</p>
</li>
<li>
<p><a href="">#12667</a>: Fixed a regression where type change in [ExceptionInfo.errisinstance]{.title-ref} caused [mypy]{.title-ref} to fail.</p>
</li>
<li>
<p><a href="">#12744</a>: Fixed typing compatibility with Python 3.9 or less -- replaced [typing.Self]{.title-ref} with [typing_extensions.Self]{.title-ref} -- by <code>Avasam</code>{.interpreted-text role=&quot;user&quot;}</p>
</li>
<li>
<p><a href="">#12745</a>: Fixed an issue with backslashes being incorrectly converted in nodeid paths on Windows, ensuring consistent path handling across environments.</p>
</li>
<li>
<p><a href="">#6682</a>: Fixed bug where the verbosity levels where not being respected when printing the &quot;msg&quot; part of failed assertion (as in <code>assert condition, msg</code>).</p>
</li>
<li>
<p><a href="">#9422</a>: Fix bug where disabling the terminal plugin via <code>-p no:terminal</code> would cause crashes related to missing the <code>verbose</code> option.</p>
<p>-- by <code>GTowers1</code>{.interpreted-text role=&quot;user&quot;}</p>
</li>
</ul>
<h2>Improved documentation</h2>
<ul>
<li><a href="">#12663</a>: Clarify that the [pytest_deselected]{.title-ref} hook should be called from [pytest_collection_modifyitems]{.title-ref} hook implementations when items are deselected.</li>
<li><a href="">#12678</a>: Remove erroneous quotes from [tmp_path_retention_policy]{.title-ref} example in docs.</li>
</ul>
<h2>Miscellaneous internal changes</h2>
<ul>
<li><a href="">#12769</a>: Fix typos discovered by codespell and add codespell to pre-commit hooks.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d0f136f</code></a> build(deps): Bump pypa/gh-action-pypi-publish from 1.10.0 to 1.10.1 (<a href="">#12790</a>)</li>
<li><a href=""><code>972f307</code></a> Prepare release version 8.3.3</li>
<li><a href=""><code>0dabdcf</code></a> Include co-authors in release announcement (<a href="">#12795</a>) (<a href="">#12797</a>)</li>
<li><a href=""><code>a9910a4</code></a> Do not discover properties when iterating fixtures (<a href="">#12781</a>) (<a href="">#12788</a>)</li>
<li><a href=""><code>0f10b6b</code></a> Fix issue with slashes being turned into backslashes on Windows (<a href="">#12760</a>) (<a href="">#12</a>...</li>
<li><a href=""><code>300d13d</code></a> Merge pull request <a href="">#12785</a> from pytest-dev/patchback/backports/8.3.x/57cccf7f4...</li>
<li><a href=""><code>e5d32c7</code></a> Merge pull request <a href="">#12784</a> from svenevs/fix/docs-example-parametrize-minor-typo</li>
<li><a href=""><code>bc913d1</code></a> Streamline checks for verbose option (<a href="">#12706</a>) (<a href="">#12778</a>)</li>
<li><a href=""><code>01cfcc9</code></a> Fix typos and introduce codespell pre-commit hook (<a href="">#12769</a>) (<a href="">#12774</a>)</li>
<li><a href=""><code>4873394</code></a> doc: Remove past training (<a href="">#12772</a>) (<a href="">#12773</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.3.2...8.3.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.3.2&new-version=8.3.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `122f74a94498`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.