# Issue

**Title:** build(deps-dev): bump jupyterlab from 4.4.0 to 4.4.8

## Description

Bumps [jupyterlab](https://github.com/jupyterlab/jupyterlab) from 4.4.0 to 4.4.8.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/jupyterlab/jupyterlab/releases">jupyterlab's releases</a>.</em></p>
<blockquote>
<h2>v4.4.8</h2>
<h2>4.4.8</h2>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/compare/v4.4.7...526a3d7f7038ed24903bf9c88b9df3e061c65b28">Full Changelog</a>)</p>
<h3>Bugs fixed</h3>
<ul>
<li>Debugger: Only send the <code>configurationDone</code> message once as per the DAP <a href="">#17912</a> (<a href="https://github.com/martinRenou"><code>@​martinRenou</code></a>)</li>
<li>Fix output prompt overlay height for large outputs <a href="">#17863</a> (<a href="https://github.com/Meriem-BenIsmail"><code>@​Meriem-BenIsmail</code></a>)</li>
<li>Prevent overlay of content from other columns when renaming a file in the file browser <a href="">#17857</a> (<a href="https://github.com/CrafterKolyan"><code>@​CrafterKolyan</code></a>)</li>
<li>Fix notebook toolbar item order <a href="">#17866</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Ignore npmjs.com in check-links <a href="">#17915</a> (<a href="https://github.com/jtpio"><code>@​jtpio</code></a>)</li>
</ul>
<h3>Documentation improvements</h3>
<ul>
<li>Add JupyterCon banner and Jupyter colors <a href="">#17906</a> (<a href="https://github.com/choldgraf"><code>@​choldgraf</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/graphs/contributors?from=2025-09-03&amp;to=2025-09-25&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Abrichet+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​brichet</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Agithub-actions+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​github-actions</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3AHaudinFlorence+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​HaudinFlorence</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Ajtpio+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​jtpio</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Ajupyterlab-probot+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​jupyterlab-probot</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Akrassowski+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​krassowski</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3AmartinRenou+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​martinRenou</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Ameeseeksmachine+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​meeseeksmachine</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3AMeriem-BenIsmail+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​Meriem-BenIsmail</code></a> | <a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Awilliamstein+updated%3A2025-09-03..2025-09-25&amp;type=Issues"><code>@​williamstein</code></a></p>
<h2>v4.4.7</h2>
<h2>4.4.7</h2>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/compare/v4.4.6...983e1c3b5849b6e8ce8d92b161917bd22fdb7937">Full Changelog</a>)</p>
<h3>Enhancements made</h3>
<ul>
<li>Update to mermaid 11.10, marked 16.2 <a href="">#17813</a> (<a href="https://github.com/bollwyvl"><code>@​bollwyvl</code></a>)</li>
</ul>
<h3>Bugs fixed</h3>
<ul>
<li>Change default line wrap in default editor config <a href="">#17818</a> (<a href="https://github.com/gjmooney"><code>@​gjmooney</code></a>)</li>
<li>Select file and accept dialog on file double click in <code>FileDialog.getOpenFiles</code> <a href="">#17844</a> (<a href="https://github.com/martinRenou"><code>@​martinRenou</code></a>)</li>
<li>Fix broken toolbar updates due to missing <code>'clear'</code> cases in switch statements for <code>ObservableList</code> <a href="">#17837</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>)</li>
<li>Send code to console <a href="">#17824</a> (<a href="https://github.com/gjmooney"><code>@​gjmooney</code></a>)</li>
<li>Clear incomplete execution metadata when splitting running cells <a href="">#17804</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>)</li>
<li>Don't create empty page_config in sys_prefix when disabled is empty <a href="">#17791</a> (<a href="https://github.com/gjmooney"><code>@​gjmooney</code></a>)</li>
</ul>
<h3>Documentation improvements</h3>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a889bb5</code></a> [ci skip] Publish 4.4.8</li>
<li><a href=""><code>51c585b</code></a> Fix integrity</li>
<li><a href=""><code>f8841dc</code></a> Merge commit from fork</li>
<li><a href=""><code>526a3d7</code></a> Backport PR <a href="">#17915</a>: Ignore npmjs.com in check-links (<a href="">#17921</a>)</li>
<li><a href=""><code>911ff90</code></a> Backport PR <a href="">#17912</a>: Debugger: Only send the <code>configurationDone</code> message once ...</li>
<li><a href=""><code>2d0ff31</code></a> Backport PR <a href="">#17906</a>: Add JupyterCon banner and Jupyter colors (<a href="">#17908</a>)</li>
<li><a href=""><code>276b38c</code></a> Backport PR <a href="">#17863</a>: Fix output prompt overlay height for large outputs (<a href="">#17889</a>)</li>
<li><a href=""><code>88f58b1</code></a> Backport PR <a href="">#17857</a>: Prevent overlay of content from other columns when renami...</li>
<li><a href=""><code>baf78ec</code></a> Backport PR <a href="">#17866</a>: Fix notebook toolbar item order (<a href="">#17872</a>)</li>
<li><a href=""><code>30d1f70</code></a> [ci skip] Publish 4.4.7</li>
<li>Additional commits viewable in <a href="https://github.com/jupyterlab/jupyterlab/compare/@jupyterlab/lsp@4.4.0...@jupyterlab/lsp@4.4.8">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=jupyterlab&package-manager=pip&previous-version=4.4.0&new-version=4.4.8)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lisphilar/covid19-sir/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f58518d9f8f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.