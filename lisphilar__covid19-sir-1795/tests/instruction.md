# Issue

**Title:** build(deps): bump optuna from 4.1.0 to 4.2.0

## Description

Bumps [optuna](https://github.com/optuna/optuna) from 4.1.0 to 4.2.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v4.2.0</h2>
<p>This is the release note of <a href="https://github.com/optuna/optuna/releases/tag/v4.2.0">v4.2.0</a>. In conjunction with the Optuna release, OptunaHub 0.2.0 is released. Please refer to <a href="https://github.com/optuna/optunahub/releases/tag/v0.2.0">the release note of OptunaHub 0.2.0</a> for more details.</p>
<p>Highlights of this release include:</p>
<ul>
<li>🚀gRPC Storage Proxy for Scalable Hyperparameter Optimization</li>
<li>🤖 SMAC3: Support for New State-of-the-art Optimization Algorithm by AutoML.org (<a href="https://github.com/automl"><code>@​automl</code></a>)</li>
<li>📁 OptunaHub Now Supports Benchmark Functions</li>
<li>🧑‍💻 Gaussian Process-Based Bayesian Optimization with Inequality Constraints</li>
<li>🧑‍💻 c-TPE: Support Constrained TPESampler</li>
</ul>
<h1>Highlights</h1>
<h2>gRPC Storage Proxy for Scalable Hyperparameter Optimization</h2>
<p>The gRPC storage proxy is a feature designed to support large-scale distributed optimization. As shown in the diagram below, gRPC storage proxy sits between the optimization workers and the database server, proxying the calls of Optuna’s storage APIs.</p>
<!-- raw HTML omitted -->
<p>In large-scale distributed optimization settings where hundreds to thousands of workers are operating, placing a gRPC storage proxy for every few tens can significantly reduce the load on the RDB server which would otherwise be a single point of failure. The gRPC storage proxy enables sharing the cache about Optuna studies and trials, which can further mitigate load. Please refer to <a href="https://optuna.readthedocs.io/en/latest/reference/generated/optuna.storages.GrpcStorageProxy.html#optuna.storages.GrpcStorageProxy">the official documentation</a> for further details on how to utilize gRPC storage proxy.</p>
<h2>SMAC3: Random Forest-Based Bayesian Optimization Developed by AutoML.org</h2>
<p><a href="https://github.com/automl/SMAC3">SMAC3</a> is a hyperparameter optimization framework developed by <a href="http://automl.org/">AutoML.org</a>, one of the most influential AutoML research groups. The Optuna-compatible SMAC3 sampler is now available thanks to the contribution to OptunaHub by Difan Deng (<a href="https://github.com/dengdifan"><code>@​dengdifan</code></a>), one of the core members of AutoML.org. We can now use the method widely used in AutoML research and real-world applications from Optuna.</p>
<pre lang="python"><code># pip install optunahub smac
import optuna
import optunahub
from optuna.distributions import FloatDistribution
<p>def objective(trial: optuna.Trial) -&gt; float:<br />
x = trial.suggest_float(&quot;x&quot;, -10, 10)<br />
y = trial.suggest_float(&quot;y&quot;, -10, 10)<br />
return x<strong>2 + y</strong>2</p>
<p>smac_mod = optunahub.load_module(&quot;samplers/smac_sampler&quot;)<br />
n_trials = 100<br />
sampler = smac_mod.SMACSampler(<br />
{&quot;x&quot;: FloatDistribution(-10, 10), &quot;y&quot;: FloatDistribution(-10, 10)},<br />
n_trials=n_trials,<br />
)<br />
study = optuna.create_study(sampler=sampler)<br />
study.optimize(objective, n_trials=n_trials)<br />
</code></pre></p>
<p>Please refer to <a href="https://hub.optuna.org/samplers/smac_sampler/">https://hub.optuna.org/samplers/smac_sampler/</a> for more details.</p>
<h2>OptunaHub Now Supports Benchmark Functions</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>13ebffa</code></a> Merge pull request <a href="">#5926</a> from c-bata/release-v4.2.0</li>
<li><a href=""><code>4d2e6c9</code></a> Bump the version up to v4.2.0</li>
<li><a href=""><code>8be82d0</code></a> Merge pull request <a href="">#5913</a> from HideakiImamura/avoid-port-number-conflict-for-c...</li>
<li><a href=""><code>92df0b2</code></a> changed the name to the camel case</li>
<li><a href=""><code>1272d7d</code></a> Simplify annotations</li>
<li><a href=""><code>f3af33d</code></a> Fix</li>
<li><a href=""><code>f2f7f0d</code></a> Add RuntimeError for try-catch</li>
<li><a href=""><code>a853c73</code></a> Merge pull request <a href="">#5924</a> from c-bata/fix-load-study-sampler-multi-objective</li>
<li><a href=""><code>2f78d5a</code></a> Fix the default sampler of load_study func</li>
<li><a href=""><code>514b174</code></a> Introduce sphinx-notfound-page for better 404 page</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v4.1.0...v4.2.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=optuna&package-manager=pip&previous-version=4.1.0&new-version=4.2.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Update Optuna to v4.2.0.

New Features:
- Introduce gRPC storage proxy for scalable hyperparameter optimization.
- Add SMAC3: Random Forest-Based Bayesian Optimization developed by AutoML.org.
- Support benchmark functions in OptunaHub.
- Enable Gaussian Process-Based Bayesian Optimization with inequality constraints.
- Support constrained TPESampler with c-TPE.

Tests:
- Avoid port number conflict for CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c3e575a846e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.