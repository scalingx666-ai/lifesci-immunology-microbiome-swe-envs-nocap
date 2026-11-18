# Issue

**Title:** build(deps-dev): bump pytest from 8.3.5 to 8.4.0

## Description

Bumps [pytest](https://github.com/pytest-dev/pytest) from 8.3.5 to 8.4.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/pytest-dev/pytest/releases">pytest's releases</a>.</em></p>
<blockquote>
<h2>8.4.0</h2>
<h1>pytest 8.4.0 (2025-06-02)</h1>
<h2>Removals and backward incompatible breaking changes</h2>
<ul>
<li>
<p><a href="">#11372</a>: Async tests will now fail, instead of warning+skipping, if you don't have any suitable plugin installed.</p>
</li>
<li>
<p><a href="">#12346</a>: Tests will now fail, instead of raising a warning, if they return any value other than None.</p>
</li>
<li>
<p><a href="">#12874</a>: We dropped support for Python 3.8 following its end of life (2024-10-07).</p>
</li>
<li>
<p><a href="">#12960</a>: Test functions containing a yield now cause an explicit error. They have not been run since pytest 4.0, and were previously marked as an expected failure and deprecation warning.</p>
<p>See <code>the docs &lt;yield tests deprecated&gt;</code>{.interpreted-text role=&quot;ref&quot;} for more information.</p>
</li>
</ul>
<h2>Deprecations (removal in next major release)</h2>
<ul>
<li><a href="">#10839</a>: Requesting an asynchronous fixture without a [pytest_fixture_setup]{.title-ref} hook that resolves it will now give a DeprecationWarning. This most commonly happens if a sync test requests an async fixture. This should have no effect on a majority of users with async tests or fixtures using async pytest plugins, but may affect non-standard hook setups or <code>autouse=True</code>. For guidance on how to work around this warning see <code>sync-test-async-fixture</code>{.interpreted-text role=&quot;ref&quot;}.</li>
</ul>
<h2>New features</h2>
<ul>
<li>
<p><a href="">#11538</a>: Added <code>pytest.RaisesGroup</code>{.interpreted-text role=&quot;class&quot;} as an equivalent to <code>pytest.raises</code>{.interpreted-text role=&quot;func&quot;} for expecting <code>ExceptionGroup</code>{.interpreted-text role=&quot;exc&quot;}. Also adds <code>pytest.RaisesExc</code>{.interpreted-text role=&quot;class&quot;} which is now the logic behind <code>pytest.raises</code>{.interpreted-text role=&quot;func&quot;} and used as parameter to <code>pytest.RaisesGroup</code>{.interpreted-text role=&quot;class&quot;}. <code>RaisesGroup</code> includes the ability to specify multiple different expected exceptions, the structure of nested exception groups, and flags for emulating <code>except* &lt;except_star&gt;</code>{.interpreted-text role=&quot;ref&quot;}. See <code>assert-matching-exception-groups</code>{.interpreted-text role=&quot;ref&quot;} and docstrings for more information.</p>
</li>
<li>
<p><a href="">#12081</a>: Added <code>capteesys</code>{.interpreted-text role=&quot;fixture&quot;} to capture AND pass output to next handler set by <code>--capture=</code>.</p>
</li>
<li>
<p><a href="">#12504</a>: <code>pytest.mark.xfail</code>{.interpreted-text role=&quot;func&quot;} now accepts <code>pytest.RaisesGroup</code>{.interpreted-text role=&quot;class&quot;} for the <code>raises</code> parameter when you expect an exception group. You can also pass a <code>pytest.RaisesExc</code>{.interpreted-text role=&quot;class&quot;} if you e.g. want to make use of the <code>check</code> parameter.</p>
</li>
<li>
<p><a href="">#12713</a>: New [--force-short-summary]{.title-ref} option to force condensed summary output regardless of verbosity level.</p>
<p>This lets users still see condensed summary output of failures for quick reference in log files from job outputs, being especially useful if non-condensed output is very verbose.</p>
</li>
<li>
<p><a href="">#12749</a>: pytest traditionally collects classes/functions in the test module namespace even if they are imported from another file.</p>
<p>For example:</p>
<pre lang="python"><code># contents of src/domain.py
class Testament: ...
<h1>contents of tests/test_testament.py</h1>
<p>from domain import Testament</p>
<p>def test_testament(): ...
</code></pre></p>
<p>In this scenario with the default options, pytest will collect the class [Testament]{.title-ref} from [tests/test_testament.py]{.title-ref} because it starts with [Test]{.title-ref}, even though in this case it is a production class being imported in the test module namespace.</p>
<p>This behavior can now be prevented by setting the new <code>collect_imported_tests</code>{.interpreted-text role=&quot;confval&quot;} configuration option to <code>false</code>, which will make pytest collect classes/functions from test files <strong>only</strong> if they are defined in that file.</p>
</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>315b3ae</code></a> Prepare release version 8.4.0</li>
<li><a href=""><code>1498ba3</code></a> Merge pull request <a href="">#13467</a> from pytest-dev/towncrier-create</li>
<li><a href=""><code>e4389ac</code></a> Remove resultlog from the docs (<a href="">#13465</a>)</li>
<li><a href=""><code>64b2301</code></a> scripts/release: add missing <code>build</code> to <code>towncrier</code> call</li>
<li><a href=""><code>4c205cf</code></a> testing/plugins_integration: update Django (<a href="">#13463</a>)</li>
<li><a href=""><code>4dcbcc9</code></a> Merge pull request <a href="">#13458</a> from pytest-dev/dup-param-error</li>
<li><a href=""><code>5293016</code></a> Merge pull request <a href="">#13459</a> from pytest-dev/pyright-minor-fixes</li>
<li><a href=""><code>7a48181</code></a> Add pyright configuration</li>
<li><a href=""><code>9fc6db9</code></a> pytester: avoid confusing <code>x</code> self parameter</li>
<li><a href=""><code>9aa198b</code></a> mark/expression: fix self -&gt; cls</li>
<li>Additional commits viewable in <a href="https://github.com/pytest-dev/pytest/compare/8.3.5...8.4.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=pytest&package-manager=pip&previous-version=8.3.5&new-version=8.4.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump pytest from 8.3.5 to 8.4.0 in poetry.lock.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd8df60c71d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.