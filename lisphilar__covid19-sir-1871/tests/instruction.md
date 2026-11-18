# Issue

**Title:** build(deps): bump optuna from 4.5.0 to 4.6.0

## Description

Bumps [optuna](https://github.com/optuna/optuna) from 4.5.0 to 4.6.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v4.6.0</h2>
<p>This is the release note of <a href="https://github.com/optuna/optuna/milestone/71?closed=1">v4.6.0</a>.</p>
<h1>Highlights</h1>
<h2>Optuna Dashboard LLM Integration</h2>
<p><a href="https://github.com/optuna/optuna-dashboard">Optuna Dashboard</a> is a web-based tool that helps you easily explore and visualize your Optuna optimization history. The latest release, v0.20.0, introduces LLM integration, enabling the natural language-based Trial filtering and automatic Plotly chart generation. Please refer to the release blog for more details.</p>
<!-- raw HTML omitted -->
<h2>Further Speed Enhancements for <code>GPSampler</code></h2>
<p><code>GPSampler</code> becomes significantly faster owing to parallelized multi-start acquisition function optimization via PyTorch batching, and to optimized NumPy operations.</p>
<!-- raw HTML omitted -->
<h2>Full Support for Multi-objective and Constrained Optimization in AutoSampler</h2>
<p>We have fully implemented sampler selection rules for multi-objective and constrained optimization in <a href="https://hub.optuna.org/samplers/auto_sampler/">AutoSampler</a>. For more details, please see our blog post, <a href="https://medium.com/optuna/autosampler-full-support-for-multi-objective-constrained-optimization-c1c4fc957ba2">&quot;AutoSampler: Full Support for Multi-Objective &amp; Constrained Optimization.&quot;</a></p>
<!-- raw HTML omitted -->
<h2>Additions of Robust Bayesian Optimization Packages</h2>
<p>Robust Bayesian optimization methods have been added to OptunaHub. Robust Bayesian optimization enables suggesting more robust parameters against input perturbations. This is especially helpful for Sim2Real transfer scenarios.</p>
<!-- raw HTML omitted -->
<h1>Breaking Changes</h1>
<ul>
<li>Drop Python 3.8 &amp; Support Python 3.13 (<a href="">optuna/optuna-integration#253</a>)</li>
<li>Change <code>TrialState.__repr__</code> and <code>TrialState.__str__</code> (<a href="">#6281</a>, thanks <a href="https://github.com/ktns"><code>@​ktns</code></a>!)</li>
<li>Drop Python 3.8 (<a href="">#6302</a>)</li>
</ul>
<h1>Enhancements</h1>
<ul>
<li>Use iterator for lazy evaluation in journal storage’s <code>read_logs</code> (<a href="">#6144</a>)</li>
<li>Cache pair-wise distances to speed up <code>GPSampler</code> (<a href="">#6244</a>)</li>
<li>Speed up LogEI implementation (<a href="">#6248</a>)</li>
<li>Speed up EHVI by optimizing tensor operation order (<a href="">#6257</a>)</li>
<li>Use the decremental approach in the hypervolume contribution calculation (<a href="">#6264</a>)</li>
<li>Use cached trials in <code>TPESampler</code>'s <code>sample_relative</code> (<a href="">#6265</a>)</li>
<li>Remove <code>find_or_raise_by_id</code> in <code>_set_trial_value_without_commit</code> (<a href="">#6266</a>)</li>
<li>Speed up <code>GPSampler</code> by Batching Acquisition Function Evaluations (<a href="">#6268</a>, thanks <a href="https://github.com/Kaichi-Irie"><code>@​Kaichi-Irie</code></a>!)</li>
<li>Use cached study direction and trial for <code>_CachedStorage</code>'s <code>get_best_trial</code> (<a href="">#6270</a>)</li>
<li>Add upsert in <code>_set_trial_attr_without_commit</code> for PostgreSQL (<a href="">#6282</a>, thanks <a href="https://github.com/jaikumarm"><code>@​jaikumarm</code></a>!)</li>
<li>Add <code>states</code> argument to <code>_read_trials_from_remote_storage</code> (<a href="">#6288</a>)</li>
<li>Use cached trials for intersection search space calculation (<a href="">#6291</a>)</li>
<li>Replace <code>np.linalg.inv</code> with <code>np.linalg.cholesky</code> to speed up <code>GPSampler</code> for <code>numpy&gt;=2.0.0</code> (<a href="">#6296</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3da7487</code></a> Merge pull request <a href="">#6324</a> from nabenabe0928/bump-up-to-v4.6.0</li>
<li><a href=""><code>ddf7fc1</code></a> Bump up to version number 4.6.0</li>
<li><a href=""><code>0765893</code></a> Merge pull request <a href="">#6323</a> from Jongwan93/format-to-fstring-_percentile.py</li>
<li><a href=""><code>1408cc7</code></a> suggestion added</li>
<li><a href=""><code>7e5f708</code></a> Merge pull request <a href="">#6321</a> from nabenabe0928/fix-exhaustive-search</li>
<li><a href=""><code>d69de4b</code></a> refactor .format to fstring in _percentile.py</li>
<li><a href=""><code>103db7d</code></a> Add safety guard for exhaustive search</li>
<li><a href=""><code>b5d1139</code></a> Merge pull request <a href="">#6319</a> from y0z/feature/updat-readme-news</li>
<li><a href=""><code>1f55093</code></a> Update NEWS section</li>
<li><a href=""><code>3073e43</code></a> Merge pull request <a href="">#6304</a> from nabenabe0928/refactor-emmr</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v4.5.0...v4.6.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=optuna&package-manager=pip&previous-version=4.5.0&new-version=4.6.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93f22e51e2a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.