# Issue

**Title:** build(deps): update optuna requirement from <5.0,>=3.5 to >=3.5,<6.0

## Description

Updates the requirements on [optuna](https://github.com/optuna/optuna) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v5.0.0</h2>
<p>This is the release note for <a href="https://github.com/optuna/optuna/milestone/76?closed=1">v5.0.0</a>.</p>
<h1>Highlights</h1>
<h2>Major Enhancements to the Default Sampler</h2>
<p>Optuna v5.0 introduces the first major update to its default sampler configuration since v1.5. For single-objective optimization, TPESampler now enables <a href="https://tech.preferred.jp/en/blog/multivariate-tpe-makes-optuna-even-more-powerful/">multivariate TPE</a> (<a href="">#6746</a>) and the constant liar strategy by default (<a href="">#6738</a>), together with enhanced bandwidth computation (<a href="https://arxiv.org/abs/2304.11127">Watanabe 2023</a>). For multi-objective optimization, TPESampler replaces NSGAIISampler as the default sampler (<a href="">#6766</a>). These settings were selected through comprehensive benchmarking to improve optimization performance.</p>
<!-- raw HTML omitted -->
<h2>New Core APIs for Constrained Optimization</h2>
<p>Constrained optimization is now represented directly in Optuna’s core Trial API. Constraint values can be set inside the objective function using <code>trial.set_constraint()</code> and retrieved through <code>trial.constraints</code>, providing a consistent interface across supported samplers. Accordingly, the sampler-specific <code>constraints_func</code> arguments are now deprecated. (<a href="">#6736</a>, <a href="">#6754</a>, <a href="">#6773</a>)</p>
<h2>PED-ANOVA Becomes the Default Parameter Importance Evaluator</h2>
<p>Optuna v5.0 makes PedAnovaImportanceEvaluator the default evaluator used by <code>optuna.importance.get_param_importances()</code>, replacing f-ANOVA. PED-ANOVA computes parameter importances substantially faster, works with Optuna’s standard dependencies, and now supports conditional search spaces and multi-objective studies. The conditional extension, <a href="https://dl.acm.org/doi/10.1145/3770855.3817758">Conditional PED-ANOVA: Hyperparameter Importance in Hierarchical &amp; Dynamic Search Spaces</a>, was accepted at KDD 2026. (<a href="">#6682</a>, <a href="">#6728</a>, <a href="">#6748</a>)</p>
<h2>Improved Parallel Optimization with GPSampler</h2>
<p><code>GPSampler</code>, now a stable API in Optuna v5.0, introduces Monte Carlo-based q-batch acquisition functions that account for trials currently under evaluation. Rather than assigning each running trial a single heuristic pseudo-value, these acquisition functions integrate over possible outcomes sampled from the Gaussian process posterior, allowing predictive uncertainty to inform subsequent suggestions.</p>
<p>The new acquisition functions cover all four major problem settings: qLogEI for unconstrained single-objective optimization, qLogCEI for constrained single-objective optimization, qLogEHVI for unconstrained multi-objective optimization, and qLogCEHVI for constrained multi-objective optimization. This provides a more principled approach to parallel Bayesian optimization across the problem settings supported by GPSampler. (<a href="">#6715</a>, <a href="">#6640</a>, <a href="">#6744</a>, <a href="">#6792</a>, <a href="">#6804</a>)</p>
<!-- raw HTML omitted -->
<h1>Breaking Changes</h1>
<ul>
<li>Remove <code>optuna.multi_objective</code> module (<a href="">#6686</a>)</li>
<li>Remove deprecated integration wrappers for AllenNLP, Chainer, and MXNet (<a href="">#6693</a>)</li>
<li>Stabilize <code>GPSampler</code> (<a href="">#6715</a>)</li>
<li>Enable <code>constant_liar</code> by default (<a href="">#6738</a>)</li>
<li>Support categorical parameters in <code>QMCSampler</code> (<a href="">#6742</a>, thanks <a href="https://github.com/saivedant169"><code>@​saivedant169</code></a>!)</li>
<li>Enable multivariate by default in <code>TPESampler</code> (<a href="">#6746</a>)</li>
<li>Remove deprecated positional-arg compatibility from study and trial APIs (<a href="">#6747</a>, thanks <a href="https://github.com/yen-0"><code>@​yen-0</code></a>!)</li>
<li>Make <code>PedAnovaImportanceEvaluator</code> the default importance evaluator (<a href="">#6748</a>)</li>
<li>Make <code>TPESampler</code> the default sampler for multi-objective optimization (<a href="">#6766</a>)</li>
<li>Deprecate <code>constraints_func</code> (<a href="">#6773</a>)</li>
<li>Change to treat cases without constraints as feasible (<a href="">#6774</a>)</li>
<li>Normalize trial timestamps to UTC in <code>RDBStorage</code> and <code>JournalStorage</code> (<a href="">#6776</a>)</li>
<li>Remove <code>axis_order</code> argument from <code>plot_pareto_front</code> (<a href="">#6781</a>)</li>
<li>Remove <code>system_attrs</code> from <code>StudySummary</code> (<a href="">#6782</a>)</li>
<li>Remove <code>categorical_distance_func</code> from <code>TPESampler</code> (<a href="">#6783</a>)</li>
<li>Remove deprecated modules (<a href="">optuna/optuna-integration#293</a>)</li>
<li>Remove <code>MXNetPruningCallback</code> (<a href="">optuna/optuna-integration#294</a>)</li>
<li>Use <code>constraints</code> property in <code>BoTorchSampler</code> (<a href="">optuna/optuna-integration#306</a>)</li>
<li>Remove <code>set_system_attr</code> and <code>system_attrs</code> from <code>TorchDistributedTrial</code> (<a href="">optuna/optuna-integration#309</a>)</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>01ddd17</code></a> Merge pull request <a href="">#6839</a> from c-bata/ignore-sphinx-warning</li>
<li><a href=""><code>1339d2c</code></a> Merge pull request <a href="">#6840</a> from y0z/feature/bump-up-version-v5</li>
<li><a href=""><code>4c975c0</code></a> Bump up version to 5.0.0</li>
<li><a href=""><code>86a1d43</code></a> Temporarily disable -W option on Sphinx build</li>
<li><a href=""><code>6ac05f5</code></a> Merge pull request <a href="">#6799</a> from yen-0/fix/cliplow</li>
<li><a href=""><code>ab320b6</code></a> Merge pull request <a href="">#6804</a> from sawa3030/add-constrained-qlogehvi</li>
<li><a href=""><code>3dbb1d5</code></a> Merge branch 'master' of <a href="https://github.com/optuna/optuna">https://github.com/optuna/optuna</a> into add-constraine...</li>
<li><a href=""><code>027f3b1</code></a> Merge pull request <a href="">#6834</a> from not522/remove-system-attr</li>
<li><a href=""><code>0576faf</code></a> Update document</li>
<li><a href=""><code>8f98dd9</code></a> Update optuna/_gp/acqf.py</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v3.5.0...v5.0.0">compare view</a></li>
</ul>
</details>
<br />

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
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5efa948a7567`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.