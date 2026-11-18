# Issue

**Title:** build(deps): bump optuna from 3.6.1 to 4.0.0

## Description

Bumps [optuna](https://github.com/optuna/optuna) from 3.6.1 to 4.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/optuna/optuna/releases">optuna's releases</a>.</em></p>
<blockquote>
<h2>v4.0.0</h2>
<p>Here is the release note of <a href="https://github.com/optuna/optuna/milestone/63?closed=1">v4.0.0</a>. Please also check out the <a href="https://medium.com/optuna/announcing-optuna-4-0-3325a8420d10">release blog post</a>.</p>
<p>If you want to update the Optuna version of your existing projects to v4.0, please see the <a href="https://github.com/optuna/optuna/discussions/5573">migration guide</a>.</p>
<p>We have also published blog posts about the development items. Please check them out!</p>
<ul>
<li><a href="https://medium.com/optuna/optunahub-a-feature-sharing-platform-for-optuna-now-available-in-official-release-4b99efe9934d">OptunaHub, a Feature-Sharing Platform for Optuna, Now Available in Official Release!</a></li>
<li><a href="https://medium.com/optuna/file-management-during-llm-large-language-model-trainings-by-optuna-v4-0-0-artifact-store-5bdd5112f3c7">File Management during LLM (Large Language Model) Trainings by Optuna v4.0.0 Artifact Store</a></li>
<li><a href="https://medium.com/optuna/significant-speed-up-of-multi-objective-tpesampler-in-optuna-v4-0-0-2bacdcd1d99b">Significant Speed Up of Multi-Objective TPESampler in Optuna v4.0.0</a></li>
</ul>
<h1>Highlights</h1>
<h2>Official Release of Feature-Sharing Platform OptunaHub</h2>
<p>We officially released <a href="https://hub.optuna.org/">OptunaHub</a>, a feature-sharing platform for Optuna. A large number of optimization and visualization algorithms are available in OptunaHub. Contributors can easily register their methods and deliver them to Optuna users around the world.</p>
<p>Please also read the <a href="https://medium.com/optuna/optunahub-a-feature-sharing-platform-for-optuna-now-available-in-official-release-4b99efe9934d">OptunaHub release blog post</a>.</p>
<p><img src="https://github.com/user-attachments/assets/7995c15b-89e6-474a-ba75-56888ae67230" alt="optunahub" /></p>
<h2>Enhanced Experiment Management Feature: Official Support of Artifact Store</h2>
<p>Artifact Store is a file management feature for files generated during optimization, dubbed artifacts. In Optuna v4.0, we stabilized the existing file upload API and further enhanced the usability of Artifact Store by adding some APIs such as the artifact download API. We also added features to show JSONL and CSV files on <a href="https://github.com/optuna/optuna-dashboard">Optuna Dashboard</a> in addition to the existing support for images, audio, and video. With this official support, the API backward compatibility will be guaranteed.</p>
<p>For more details, please check the <a href="https://medium.com/optuna/file-management-during-llm-large-language-model-trainings-by-optuna-v4-0-0-artifact-store-5bdd5112f3c7">blog post</a>.</p>
<p><img src="https://github.com/user-attachments/assets/1556ef5a-852a-4256-b2e7-32c7d2eef253" alt="artifact" /></p>
<h2><code>JournalStorage</code>: Official Support of Distributed Optimization via Network File System</h2>
<p><code>JournalStorage</code> is a new Optuna storage experimentally introduced in Optuna v3.1 (see the <a href="https://medium.com/optuna/distributed-optimization-via-nfs-using-optunas-new-operation-based-logging-storage-9815f9c3f932">blog post</a> for details). Optuna has <code>JournalFileBackend</code>, a storage backend for various file systems. It can be used on NFS, allowing Optuna to scale to multiple nodes.</p>
<p>In Optuna v4.0, the API for <code>JournalStorage</code> has been reorganized, and <code>JournalStorage</code> is officially supported. This official support guarantees its backward compatibility from v4.0. For details on the API changes, please refer to the <a href="https://github.com/optuna/optuna/discussions/5573">Optuna v4.0 Migration Guide</a>.</p>
<pre lang="python"><code>import optuna
from optuna.storages import JournalStorage
from optuna.storages.journal import JournalFileBackend
<p>def objective(trial: optuna.Trial) -&gt; float:<br />
...</p>
<p>storage = JournalStorage(JournalFileBackend(&quot;./optuna_journal_storage.log&quot;))<br />
study = optuna.create_study(storage=storage)<br />
study.optimize(objective)<br />
</code></pre></p>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ef16a04</code></a> Merge pull request <a href="">#5653</a> from eukaryo/bump-up-to-v4.0.0</li>
<li><a href=""><code>5bb0af1</code></a> Update version.py</li>
<li><a href=""><code>e3eec34</code></a> Merge pull request <a href="">#5649</a> from eukaryo/update-news-ingo-blog</li>
<li><a href=""><code>0e6a6f0</code></a> Update README.md</li>
<li><a href=""><code>e63e336</code></a> Update README.md</li>
<li><a href=""><code>7fd30c9</code></a> Merge pull request <a href="">#5644</a> from kAIto47802/doc-add-install-visualization</li>
<li><a href=""><code>3c15a3e</code></a> Merge pull request <a href="">#5648</a> from toshihikoyanase/remove-404-link</li>
<li><a href=""><code>79201a7</code></a> Update tutorial/10_key_features/005_visualization.py</li>
<li><a href=""><code>86ee356</code></a> Update README.md</li>
<li><a href=""><code>a10b917</code></a> Merge pull request <a href="">#5637</a> from nabenabe0928/doc/add-sns-to-readme</li>
<li>Additional commits viewable in <a href="https://github.com/optuna/optuna/compare/v3.6.1...v4.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=optuna&package-manager=pip&previous-version=3.6.1&new-version=4.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `598e659ecde2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.