# Issue

**Title:** build(deps-dev): bump pytest from 8.4.2 to 9.0.1

## Description

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.4.2 to 9.0.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>9.0.1</h2>
<h1>pytest 9.0.1 (2025-11-12)</h1>
<h2>Bug fixes</h2>
<ul>
<li><a href="">#13895</a>: Restore support for skipping tests via <code>raise unittest.SkipTest</code>.</li>
<li><a href="">#13896</a>: The terminal progress plugin added in pytest 9.0 is now automatically disabled when iTerm2 is detected, it generated desktop notifications instead of the desired functionality.</li>
<li><a href="">#13904</a>: Fixed the TOML type of the verbosity settings in the API reference from number to string.</li>
<li><a href="">#13910</a>: Fixed <!-- raw HTML omitted -->UserWarning: Do not expect file_or_dir<!-- raw HTML omitted --> on some earlier Python 3.12 and 3.13 point versions.</li>
</ul>
<h2>Packaging updates and notes for downstreams</h2>
<ul>
<li><a href="">#13933</a>: The tox configuration has been adjusted to make sure the desired
version string can be passed into its <code>package_env</code> through
the <code>SETUPTOOLS_SCM_PRETEND_VERSION_FOR_PYTEST</code> environment
variable as a part of the release process -- by <code>webknjaz</code>.</li>
</ul>
<h2>Contributor-facing changes</h2>
<ul>
<li><a href="">#13891</a>, <a href="">#13942</a>: The CI/CD part of the release automation is now capable of
creating GitHub Releases without having a Git checkout on
disk -- by <code>bluetech</code> and <code>webknjaz</code>.</li>
<li><a href="">#13933</a>: The tox configuration has been adjusted to make sure the desired
version string can be passed into its <code>package_env</code> through
the <code>SETUPTOOLS_SCM_PRETEND_VERSION_FOR_PYTEST</code> environment
variable as a part of the release process -- by <code>webknjaz</code>.</li>
</ul>
<h2>9.0.0</h2>
<h1>pytest 9.0.0 (2025-11-05)</h1>
<h2>New features</h2>
<ul>
<li>
<p><a href="">#1367</a>: <strong>Support for subtests</strong> has been added.</p>
<p><code>subtests &lt;subtests&gt;</code> are an alternative to parametrization, useful in situations where the parametrization values are not all known at collection time.</p>
<p>Example:</p>
<pre lang="python"><code>def contains_docstring(p: Path) -&gt; bool:
    &quot;&quot;&quot;Return True if the given Python file contains a top-level docstring.&quot;&quot;&quot;
    ...
<p>def test_py_files_contain_docstring(subtests: pytest.Subtests) -&gt; None:<br />
for path in Path.cwd().glob(&quot;*.py&quot;):<br />
with subtests.test(path=str(path)):<br />
assert contains_docstring(path)<br />
</code></pre></p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d1b64aa</code></a> Prepare release version 9.0.1</li>
<li><a href=""><code>0a497c7</code></a> regendoc: remove CI environment variables (<a href="">#13950</a>) (<a href="">#13951</a>)</li>
<li><a href=""><code>a9f7e6e</code></a> 🧪 Run <code>gh release</code> w/o Git in CI/CD (<a href="">#13942</a>) (<a href="">#13947</a>)</li>
<li><a href=""><code>2682a66</code></a> Merge pull request <a href="">#13944</a> from pytest-dev/patchback/backports/9.0.x/bef7d34f1...</li>
<li><a href=""><code>a999997</code></a> Merge pull request <a href="">#13941</a> from nicoddemus/min-pre-commit-version</li>
<li><a href=""><code>4bd63a0</code></a> Merge pull request <a href="">#13935</a> from pytest-dev/patchback/backports/9.0.x/ce8b8a7b4...</li>
<li><a href=""><code>15f93b3</code></a> Merge pull request <a href="">#13933</a> from webknjaz/maintenance/tox-pep517-env-setuptools...</li>
<li><a href=""><code>0fa11ae</code></a> Merge pull request <a href="">#13927</a> from pytest-dev/patchback/backports/9.0.x/3d8075743...</li>
<li><a href=""><code>fa45470</code></a> Merge pull request <a href="">#13926</a> from pytest-dev/patchback/backports/9.0.x/d587e0cf8...</li>
<li><a href=""><code>b4e3973</code></a> Merge pull request <a href="">#13922</a> from bluetech/fix-argparse-userwarning</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.4.2...9.0.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.4.2&new-version=9.0.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `367d760360af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.