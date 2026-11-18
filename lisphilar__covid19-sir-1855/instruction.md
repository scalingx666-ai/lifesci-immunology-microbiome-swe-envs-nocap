# Issue

**Title:** build(deps): bump optuna from 4.4.0 to 4.5.0

## Description

Bumps [optuna](https://github.com/optuna/optuna) from 4.4.0 to 4.5.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v4.5.0</h2>
<p>This is the release note of <a href="https://github.com/optuna/optuna/milestone/70?closed=1">v4.5.0</a>.</p>
<h1>Highlights</h1>
<h2><code>GPSampler</code> for constrained multi-objective optimization</h2>
<p><code>GPSampler</code> is now able to handle multiple objective and constraints simultaneously using the newly introduced constrained LogEHVI acquisition function.</p>
<p>The figures below show the difference between <code>GPSampler</code> (LogEHVI, unconstrained) vs <code>GPSampler</code> (constrained LogEHVI, new feature). The 3-dimensional version of the C2DTLZ2 benchmark problem we used is a problem where some areas of the Pareto front of the original DTLZ2 problem are made infeasible by constraints. Therefore, even if constraints are not taken into account, it is possible to obtain the Pareto front. Experimental results show that both LogEHVI and constrained LogEHVI can approximate the Pareto front, but the latter has significantly fewer infeasible solutions, demonstrating its efficiency.</p>
<table>
<thead>
<tr>
<th align="center">Optuna v4.4 (LogEHVI)</th>
<th align="center">Optuna v4.5 (Constrained LogEHVI)</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><!-- raw HTML omitted --></td>
<td align="center"><!-- raw HTML omitted --></td>
</tr>
</tbody>
</table>
<h2>Significant speedup of <code>TPESampler</code></h2>
<p><code>TPESampler</code> is significantly (about 5x as listed in the table below) faster! It enables a larger number of trials in each study. The speedup was achieved through a series of enhancements in constant factors.</p>
<p>The following table shows the speed comparison of <code>TPESampler</code> between v4.4.0 and v4.5.0. The experiments were conducted using <code>multivariate=True</code> on a search space with 3 continuous parameters and 3 numerical discrete parameters. Each row shows the runtime for each number of objectives and each column shows each number of trials to be evaluated. Each runtime is shown along with the standard error over 3 random seeds. The numbers in parentheses represent the speedup factor in comparison to v4.4.0. For example, (5.1x) means the runtime of v4.5.0 is 5.1 times faster than that of v4.4.0.</p>
<table>
<thead>
<tr>
<th align="center"><code>n_objectives</code>/<code>n_trials</code></th>
<th align="center">500</th>
<th align="center">1000</th>
<th align="center">1500</th>
<th align="center">2000</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">1</td>
<td align="center">1.4 $\pm$ 0.03 (5.1x)</td>
<td align="center">3.9 $\pm$ 0.07 (5.3x)</td>
<td align="center">7.3 $\pm$ 0.09 (5.4x)</td>
<td align="center">11.9 $\pm$ 0.10 (5.4x)</td>
</tr>
<tr>
<td align="center">2</td>
<td align="center">1.8 $\pm$ 0.01 (4.7x)</td>
<td align="center">4.7 $\pm$ 0.02 (4.8x)</td>
<td align="center">8.7 $\pm$ 0.03 (4.8x)</td>
<td align="center">13.9 $\pm$ 0.04 (4.9x)</td>
</tr>
<tr>
<td align="center">3</td>
<td align="center">2.0 $\pm$ 0.01 (4.2x)</td>
<td align="center">5.4 $\pm$ 0.03 (4.4x)</td>
<td align="center">10.0 $\pm$ 0.03 (4.6x)</td>
<td align="center">15.9 $\pm$ 0.03 (4.7x)</td>
</tr>
<tr>
<td align="center">4</td>
<td align="center">4.2 $\pm$ 0.11 (3.2x)</td>
<td align="center">12.1 $\pm$ 0.14 (3.9x)</td>
<td align="center">20.9 $\pm$ 0.23 (4.2x)</td>
<td align="center">31.3 $\pm$ 0.05 (4.4x)</td>
</tr>
<tr>
<td align="center">5</td>
<td align="center">12.1 $\pm$ 0.59 (4.7x)</td>
<td align="center">30.8 $\pm$ 0.16 (5.8x)</td>
<td align="center">50.7 $\pm$ 0.46 (6.5x)</td>
<td align="center">72.8 $\pm$ 1.13 (7.1x)</td>
</tr>
</tbody>
</table>
<h2>Significant speedup of <code>plot_hypervolume_history</code></h2>
<p><code>plot_hypervolume_history</code> is essential to assess the performance of multi-objective optimization, but it was unbearably slow when a large number of trials are evaluated on a many-objective (The number of objectives &gt; 3) problem. v4.5.0 addressed this issue by incrementally updating the hypervolume instead of calculating each hypervolume from scratch.</p>
<p>The following figure shows the elapsed times of hypervolume history plot in Optuna v4.4.0 and v4.5.0 using a four-objective problem. The x-axis represents the number of trials and the y-axis represents the elapsed times for each setup. The blue and red lines are the results of v4.4.0 and v4.5.0, respectively.</p>
<!-- raw HTML omitted -->
<h2><code>CmaEsSampler</code> now supports 1D search space</h2>
<p>Up until Optuna v4.4, <code>CmaEsSampler</code> could not handle one-dimensional space and fell back to <em>random search</em>. Optuna v4.5 now allows the CMA-ES algorithm to be used for one-dimensional space.</p>
<h2>The optunahub library is available on conda-forge</h2>
<p>Now, you can install <a href="https://anaconda.org/conda-forge/optunahub">the optunahub library via conda-forge</a> as follows.</p>
<pre lang="sh"><code>conda install conda-forge::optunahub
</code></pre>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d7e1c1b</code></a> Merge pull request <a href="">#6251</a> from y0z/feature/bump-up-version</li>
<li><a href=""><code>ad24880</code></a> Bump up version to v4.5.0</li>
<li><a href=""><code>b706a63</code></a> Merge pull request <a href="">#6240</a> from fusawa-yugo/fusawa-yugo/lru_cache_for_hssp</li>
<li><a href=""><code>aba5302</code></a> Merge pull request <a href="">#6245</a> from nabenabe0928/hotfix/add-hv-for-zero-size</li>
<li><a href=""><code>8054dbb</code></a> Add a unit test</li>
<li><a href=""><code>eba34c9</code></a> Merge remote-tracking branch 'upstream/master' into hotfix/add-hv-for-zero-size</li>
<li><a href=""><code>a556b08</code></a> Merge pull request <a href="">#6246</a> from nabenabe0928/hotfix-ci</li>
<li><a href=""><code>268ebc1</code></a> Address c-bata's comment</li>
<li><a href=""><code>86f0c4c</code></a> revert</li>
<li><a href=""><code>8e970db</code></a> Fix</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v4.4.0...v4.5.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=optuna&package-manager=pip&previous-version=4.4.0&new-version=4.5.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aaa6c0463252`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.