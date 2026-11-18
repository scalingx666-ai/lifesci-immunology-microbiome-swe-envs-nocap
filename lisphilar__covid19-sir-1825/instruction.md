# Issue

**Title:** build(deps): bump optuna from 4.2.1 to 4.3.0

## Description

Bumps [optuna](https://github.com/optuna/optuna) from 4.2.1 to 4.3.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v4.3.0</h2>
<p>This is the release note of <a href="https://github.com/optuna/optuna/milestone/66?closed=1">v4.3.0</a>.</p>
<h1>Highlights</h1>
<p>This has various bug fixes and improvements to the documentation and more.</p>
<h1>Breaking Changes</h1>
<ul>
<li>[fix] lgbm 4.6.0 compatibility (<a href="">optuna/optuna-integration#207</a>, thanks <a href="https://github.com/ffineis"><code>@​ffineis</code></a>!)</li>
</ul>
<h1>Enhancements</h1>
<ul>
<li>Accept custom objective in <code>LightGBMTuner</code> (<a href="">optuna/optuna-integration#203</a>, thanks <a href="https://github.com/sawa3030"><code>@​sawa3030</code></a>!)</li>
<li>Improve time complexity of <code>IntersectionSearchSpace</code> (<a href="">#5982</a>, thanks <a href="https://github.com/GittyHarsha"><code>@​GittyHarsha</code></a>!)</li>
<li>Add <code>_prev_waiting_trial_number</code> in <code>InMemoryStorage</code> to improve the efficiency of <code>_pop_waiting_trial_id</code> (<a href="">#5993</a>, thanks <a href="https://github.com/sawa3030"><code>@​sawa3030</code></a>!)</li>
<li>Add arguments of versions to <code>convert_positional_args</code> (<a href="">#6009</a>, thanks <a href="https://github.com/fusawa-yugo"><code>@​fusawa-yugo</code></a>!)</li>
<li>Add <code>wait_server_ready</code> method in GrpcStorageProxy (<a href="">#6010</a>, thanks <a href="https://github.com/hitsgub"><code>@​hitsgub</code></a>!)</li>
<li>Remove warning messages for Matplotlib-based <code>plot_contour</code> and <code>plot_rank</code> (<a href="">#6011</a>)</li>
<li>Fix type checking in <code>optuna._callbacks.py</code> (<a href="">#6030</a>)</li>
<li>Enhance <code>SBXCrossover</code> (<a href="">#6008</a>, thanks <a href="https://github.com/hrntsm"><code>@​hrntsm</code></a>!)</li>
</ul>
<h1>Bug Fixes</h1>
<ul>
<li>Convert storage into <code>InMemoryStorage</code> before copying to the local (<a href="">optuna/optuna-integration#213</a>)</li>
<li>Fix contour plot of <code>matplotlib</code> (<a href="">#5892</a>, thanks <a href="https://github.com/fusawa-yugo"><code>@​fusawa-yugo</code></a>!)</li>
<li>Fix threading lock logic (<a href="">#5922</a>)</li>
<li>Use <code>_LazyImport</code> for grpcio package (<a href="">#5954</a>)</li>
<li>Prevent Lock Blocking by Adding Timeout to <code>JournalStorage</code> (<a href="">#5971</a>, thanks <a href="https://github.com/sawa3030"><code>@​sawa3030</code></a>!)</li>
<li>Fix a minor bug in GPSampler for objective that returns <code>inf</code> (<a href="">#5995</a>)</li>
<li>Fix a bug that a gRPC server doesn't work with JournalStorage (<a href="">#6004</a>, thanks <a href="https://github.com/fusawa-yugo"><code>@​fusawa-yugo</code></a>!)</li>
<li>Fix <code>_pop_waiting_trial_id</code> for finished trial (<a href="">#6012</a>)</li>
<li>Resolve the issue where <code>BruteForceSampler</code> fails to suggest all combinations (<a href="">#5893</a>)</li>
</ul>
<h1>Documentation</h1>
<ul>
<li>Follow recent changes in <code>optuna/optuna</code>'s document sphinx config (<a href="">optuna/optuna-integration#197</a>)</li>
<li>Fix links to external modules (<a href="">optuna/optuna-integration#198</a>)</li>
<li>Update <code>CONTRIBUTING.md</code> (<a href="">optuna/optuna-integration#200</a>, thanks <a href="https://github.com/sawa3030"><code>@​sawa3030</code></a>!)</li>
<li>Update comment in <code>.readthedocs.yml</code> (<a href="">#5976</a>)</li>
<li>Add comments on the reproducibility of <code>HyperBandPruner</code> (<a href="">#6018</a>)</li>
</ul>
<h1>Examples</h1>
<ul>
<li>[hotfix] Add the version constraint on <code>dask</code> (<a href="">optuna/optuna-examples#296</a>)</li>
<li>[hotfix] Add the version constraint on  <code>dask</code> for <code>dask-ml</code> (<a href="">optuna/optuna-examples#297</a>)</li>
<li>Extends execution span of <code>hiplot</code> and <code>sklearn</code> (<a href="">optuna/optuna-examples#298</a>, thanks <a href="https://github.com/fusawa-yugo"><code>@​fusawa-yugo</code></a>!)</li>
<li>Apply black to fix CI (<a href="">optuna/optuna-examples#300</a>)</li>
<li>Bump up to 3.12 for CI (<a href="">optuna/optuna-examples#301</a>)</li>
<li>[hotfix] Add the version constraint on <code>lightgbm</code> (<a href="">optuna/optuna-examples#302</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>bc23723</code></a> Merge pull request <a href="">#6037</a> from y0z/feature/bump-up-version-for-4.3</li>
<li><a href=""><code>ac4f1dd</code></a> Bump up version to 4.3.0</li>
<li><a href=""><code>11ff024</code></a> Merge pull request <a href="">#6009</a> from fusawa-yugo/fusawa-yugo/add_argument_to_convert...</li>
<li><a href=""><code>ebd8c12</code></a> Fix</li>
<li><a href=""><code>6c85b2a</code></a> revert</li>
<li><a href=""><code>19296c3</code></a> Merge pull request <a href="">#6008</a> from hrntsm/update-sbx</li>
<li><a href=""><code>acb810a</code></a> update docstring</li>
<li><a href=""><code>004f5c7</code></a> fix typo</li>
<li><a href=""><code>58fea87</code></a> Make implementation and docstring more clear</li>
<li><a href=""><code>db32402</code></a> lint</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v4.2.1...v4.3.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=optuna&package-manager=pip&previous-version=4.2.1&new-version=4.3.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Update Optuna dependency from version 4.2.1 to 4.3.0

Bug Fixes:
- Fix various threading and locking issues
- Resolve compatibility problems with different libraries
- Correct minor bugs in sampling and storage mechanisms

Enhancements:
- Improve time complexity of search space operations
- Add efficiency improvements to in-memory storage
- Enhance crossover functionality

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65ff81758576`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.