# Issue

**Title:** build(deps): bump optuna from 4.3.0 to 4.4.0

## Description

Bumps [optuna](https://github.com/optuna/optuna) from 4.3.0 to 4.4.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v4.4.0</h2>
<p>This is the release note of <a href="https://github.com/optuna/optuna/milestone/69?closed=1">v4.4.0</a>.</p>
<h1>Highlights</h1>
<p>In addition to new features, bug fixes, and improvements in documentation and testing, version 4.4 introduces a new tool called the <a href="https://github.com/optuna/optuna-mcp">Optuna MCP Server</a>.</p>
<h2>Optuna MCP Server</h2>
<p>The Optuna MCP server can be accessed by any MCP client via uv — for instance, with Claude Desktop, simply add the following configuration to your MCP server settings file. Of course, other LLM clients like VSCode or Cline can also be used similarly. You can also access it via Docker. If you want to persist the results, you can use the — storage option. For details, please refer to the <a href="https://github.com/optuna/optuna-mcp">repository</a>.</p>
<pre><code>{
  &quot;mcpServers&quot;: {
    … (Other MCP Servers' settings)
    &quot;Optuna&quot;: {
      &quot;command&quot;: &quot;uvx&quot;,
      &quot;args&quot;: [
        &quot;optuna-mcp&quot;
      ]
    }
  }
}
</code></pre>
<p><img src="https://github.com/user-attachments/assets/231165f7-5df6-4e11-8c20-c89f1da7af26" alt="image3" /></p>
<h2>Gaussian Process-Based Multi-objective Optimization</h2>
<p>Optuna’s GPSampler, introduced in version 3.6, offers superior speed and performance compared to existing Bayesian optimization frameworks, particularly when handling objective functions with discrete variables. In Optuna v4.4, we have extended this GPSampler to support multi-objective optimization problems. The applications of multi-objective optimization are broad, and the new multi-objective capabilities introduced in this GPSampler are expected to find applications in fields such as material design, experimental design problems, and high-cost hyperparameter optimization.</p>
<p>GPSampler can be easily integrated into your program and performs well against the existing BoTorchSampler. We encourage you to try it out with your multi-objective optimization problems.</p>
<pre lang="python"><code>sampler = optuna.samplers.GPSampler()
study = optuna.create_study(directions=[&quot;minimize&quot;, &quot;minimize&quot;], sampler=sampler)
</code></pre>
<p><img src="https://github.com/user-attachments/assets/24586f21-fd9c-4d8c-86db-2507f3a2c12f" alt="image2" /></p>
<h2>New Features in OptunaHub</h2>
<p>During the development period of Optuna v4.4, several new features were also introduced to OptunaHub, the feature-sharing platform for Optuna:</p>
<ul>
<li>A <a href="https://hub.optuna.org/samplers/vizier/">sampler utilizing Google Vizier</a> is now newly available.</li>
<li>The <a href="https://hub.optuna.org/samplers/restart_cmaes/">CMA-ES-based sampler with restart strategy</a>, which was previously part of the Optuna core, has been migrated to OptunaHub, making it simpler and more user-friendly.</li>
<li>A <a href="https://hub.optuna.org/benchmarks/hpa/">benchmark problem solving aircraft design</a> as a black-box optimization task has been added, further enhancing the convenience of algorithm development using OptunaHub.</li>
<li>A visualization feature has also been added, allowing users to see <a href="https://hub.optuna.org/visualization/tpe_acquisition_visualizer/">how the acquisition function of the default TPESampler evolves as trials progress</a>.</li>
<li>A novel mutation operation has been added to the <a href="https://hub.optuna.org/samplers/moead/">MOEA/D evolutionary computation algorithm</a> for multi-objective optimization.</li>
</ul>
<p>| Vizier sampler performance  |</p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>0742587</code></a> Merge pull request <a href="">#6148</a> from HideakiImamura/bump-version-4.4</li>
<li><a href=""><code>becfc27</code></a> Bump up version number to v4.4.0</li>
<li><a href=""><code>5ccdf30</code></a> Merge pull request <a href="">#6145</a> from c-bata/fix-blackdoc-checks</li>
<li><a href=""><code>f32571d</code></a> [hotfix] Add version constraint on blackdoc at reviewdog.yml</li>
<li><a href=""><code>9622bb8</code></a> [hotfix] Add version constraint on blackdoc</li>
<li><a href=""><code>cad5190</code></a> Merge pull request <a href="">#6143</a> from Shubham05122002/refactor-return-tuple-style-mod...</li>
<li><a href=""><code>42daf94</code></a> Refactor return statement style in optuna/storages/_rdb/models.py for consist...</li>
<li><a href=""><code>b0f1482</code></a> Merge pull request <a href="">#6141</a> from saishreyakumar/fix-return-tuple-test-trial</li>
<li><a href=""><code>6f528b9</code></a> Merge pull request <a href="">#6139</a> from Prashantdhaka23/fix-return-tuple</li>
<li><a href=""><code>59559cf</code></a> Merge upstream/master into fix-return-tuple-test-trial</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v4.3.0...v4.4.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=optuna&package-manager=pip&previous-version=4.3.0&new-version=4.4.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Update Poetry lock file to require Optuna v4.4.0

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dfba07928069`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.