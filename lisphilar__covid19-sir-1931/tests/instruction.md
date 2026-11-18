# Issue

**Title:** build(deps): bump jupyterlab from 4.5.7 to 4.5.9

## Description

Bumps [jupyterlab](https://github.com/jupyterlab/jupyterlab) from 4.5.7 to 4.5.9.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/jupyterlab/jupyterlab/releases">jupyterlab's releases</a>.</em></p>
<blockquote>
<h2>v4.5.9</h2>
<h2>4.5.9</h2>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/compare/v4.5.8...26936727d7f197bab4f314ca50690cd162d50312">Full Changelog</a>)</p>
<h3>Bugs fixed</h3>
<ul>
<li>Fix <code>jupyter labextension build</code> crash on <code>webpack ≥ 5.107</code> <a href="">#19021</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>, <a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
<li>Backport PR <a href="">#18992</a>: Fix hidden cells after moving collapsed headings <a href="">#19016</a> (<a href="https://github.com/MUFFANUJ"><code>@​MUFFANUJ</code></a>, <a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
<li>Forbid relative URLs in extensionmanager <a href="">#19013</a> (<a href="https://github.com/Yann-P"><code>@​Yann-P</code></a>)</li>
<li>Fix XSS in extension manager's <code>homepage_url</code> <a href="">#19003</a> (<a href="https://github.com/Yann-P"><code>@​Yann-P</code></a>)</li>
<li>Fix toolbar popup row clipping in Safari <a href="">#18998</a> (<a href="https://github.com/arun-357"><code>@​arun-357</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>The following people contributed discussions, new ideas, code and documentation contributions, and review.
See <a href="https://github-activity.readthedocs.io/en/latest/use/#how-does-this-tool-define-contributions-in-the-reports">our definition of contributors</a>.</p>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/graphs/contributors?from=2026-06-04&amp;to=2026-06-17&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/arun-357"><code>@​arun-357</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Aarun-357+updated%3A2026-06-04..2026-06-17&amp;type=Issues">activity</a>) | <a href="https://github.com/Darshan808"><code>@​Darshan808</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3ADarshan808+updated%3A2026-06-04..2026-06-17&amp;type=Issues">activity</a>) | <a href="https://github.com/krassowski"><code>@​krassowski</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Akrassowski+updated%3A2026-06-04..2026-06-17&amp;type=Issues">activity</a>) | <a href="https://github.com/MUFFANUJ"><code>@​MUFFANUJ</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3AMUFFANUJ+updated%3A2026-06-04..2026-06-17&amp;type=Issues">activity</a>) | <a href="https://github.com/Yann-P"><code>@​Yann-P</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3AYann-P+updated%3A2026-06-04..2026-06-17&amp;type=Issues">activity</a>)</p>
<h2>v4.5.8</h2>
<h2>4.5.8</h2>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/compare/v4.5.7...8d30d481fbab784096e04d85dfa3b0c36e77be2c">Full Changelog</a>)</p>
<h3>Bugs fixed</h3>
<ul>
<li>Prevent dialog from hanging when <code>getValue()</code> throws <a href="">#18938</a> (<a href="https://github.com/AliMahmoudDev"><code>@​AliMahmoudDev</code></a>)</li>
<li>Add <code>packaging</code> min version pin <a href="">#18910</a> (<a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
<li>Use CSS <code>anchor</code> for prompt overlay <a href="">#18840</a> (<a href="https://github.com/CrafterKolyan"><code>@​CrafterKolyan</code></a>)</li>
</ul>
<h3>Maintenance and upkeep improvements</h3>
<ul>
<li>Fix completer test failures on CI <a href="">#18946</a> (<a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
<li>Bump license webpack plugin <a href="">#18929</a> (<a href="https://github.com/Darshan808"><code>@​Darshan808</code></a>, <a href="https://github.com/krassowski"><code>@​krassowski</code></a>)</li>
</ul>
<h3>Contributors to this release</h3>
<p>The following people contributed discussions, new ideas, code and documentation contributions, and review.
See <a href="https://github-activity.readthedocs.io/en/latest/use/#how-does-this-tool-define-contributions-in-the-reports">our definition of contributors</a>.</p>
<p>(<a href="https://github.com/jupyterlab/jupyterlab/graphs/contributors?from=2026-04-29&amp;to=2026-06-04&amp;type=c">GitHub contributors page for this release</a>)</p>
<p><a href="https://github.com/AliMahmoudDev"><code>@​AliMahmoudDev</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3AAliMahmoudDev+updated%3A2026-04-29..2026-06-04&amp;type=Issues">activity</a>) | <a href="https://github.com/CrafterKolyan"><code>@​CrafterKolyan</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3ACrafterKolyan+updated%3A2026-04-29..2026-06-04&amp;type=Issues">activity</a>) | <a href="https://github.com/Darshan808"><code>@​Darshan808</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3ADarshan808+updated%3A2026-04-29..2026-06-04&amp;type=Issues">activity</a>) | <a href="https://github.com/krassowski"><code>@​krassowski</code></a> (<a href="https://github.com/search?q=repo%3Ajupyterlab%2Fjupyterlab+involves%3Akrassowski+updated%3A2026-04-29..2026-06-04&amp;type=Issues">activity</a>)</p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>dd65403</code></a> [ci skip] Publish 4.5.9</li>
<li><a href=""><code>2693672</code></a> Backport PR <a href="">#18992</a>: Fix hidden cells after moving collapsed headings (<a href="">#19016</a>)</li>
<li><a href=""><code>360c176</code></a> Backport PR <a href="">#18998</a> on branch 4.5.x (Fix toolbar popup row clipping in Safari)...</li>
<li><a href=""><code>e9db010</code></a> Fix <code>jupyter labextension build</code> crash on <code>webpack ≥ 5.107</code> (<a href="">#19021</a>)</li>
<li><a href=""><code>3b8428c</code></a> Backport PR <a href="">#19013</a> on branch 4.5.x (Forbid relative URLs in extensionmanager)...</li>
<li><a href=""><code>3c84a84</code></a> Backport PR <a href="">#19003</a> on branch 4.5.x (Fix XSS in extension manager's `homepage_...</li>
<li><a href=""><code>0dee996</code></a> [ci skip] Publish 4.5.8</li>
<li><a href=""><code>8d30d48</code></a> Backport PR <a href="">#18946</a> on branch 4.5.x (Fix completer test failures on CI) (<a href="">#18949</a>)</li>
<li><a href=""><code>872d4c8</code></a> Backport PR <a href="">#18938</a> on branch 4.5.x (Prevent dialog from hanging when `getValu...</li>
<li><a href=""><code>d8a3874</code></a> Bump license webpack plugin (<a href="">#18929</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/jupyterlab/jupyterlab/compare/@jupyterlab/lsp@4.5.7...@jupyterlab/lsp@4.5.9">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=jupyterlab&package-manager=uv&previous-version=4.5.7&new-version=4.5.9)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lisphilar/covid19-sir/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `674db49f4bbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.