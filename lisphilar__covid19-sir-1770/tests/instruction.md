# Issue

**Title:** build(deps-dev): bump deptry from 0.20.0 to 0.21.0

## Description

Bumps [deptry](https://github.com/fpgmaas/deptry) from 0.20.0 to 0.21.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/releases">deptry's releases</a>.</em></p>
<blockquote>
<h2>0.21.0</h2>
<h2>What's Changed</h2>
<h3>Breaking changes</h3>
<h4>Ignore files handling</h4>
<p>Unless <a href="https://deptry.com/usage/#exclude"><code>--exclude</code></a> is used, <em>deptry</em> excludes files found in common ignore files (<code>.gitignore</code>, <code>.ignore</code>, <code>$HOME/.config/git/ignore</code>. ...), by using <a href="https://crates.io/crates/ignore"><code>ignore</code></a> Rust crate. The default behaviour has been changed, so that now:</p>
<ul>
<li>git-related ignore rules (<code>.gitignore</code>, <code>$HOME/.config/git/ignore</code>, ...) are only used if <em>deptry</em> is run inside a git repository</li>
<li><code>.gitignore</code> files that are in parent directories of the git repository from where deptry is run are not used (previously, <em>deptry</em> would traverse parent directories up to the root system)</li>
</ul>
<p>If you were using <code>.gitignore</code> files for non-git repositories, you might want to switch to <code>.ignore</code> files, or use <a href="https://deptry.com/usage/#extend-exclude"><code>--extend-exclude</code></a>.</p>
<h4>Requirements files parsing</h4>
<p><em>deptry</em> now uses <a href="https://pypi.org/project/requirements-parser/"><code>requirements-parser</code></a> to parse dependencies from requirements files, meaning that it can now extract nested requirements files referenced in other requirements files without having to explicitly configure it in <em>deptry</em>.</p>
<p>For instance, if you have:</p>
<pre lang="python"><code># requirements.txt
-r cli-requirements.txt
httpx==0.27.2
</code></pre>
<pre lang="python"><code># cli-requirements.txt
click==8.1.7
</code></pre>
<p>With the default configuration, when parsing <code>requirements.txt</code>, both <code>httpx</code> and <code>click</code> will now be listed as dependencies by <em>deptry</em>, while previously, only <code>httpx</code> was, unless <em>deptry</em> was instructed about <code>cli-requirements.txt</code> by using <a href="https://deptry.com/usage/#requirements-files"><code>--requirements-files</code></a>. This new behaviour also impacts development requirements files, that can be overridden by using <a href="https://deptry.com/usage/#requirements-files-dev"><code>--requirements-files-dev</code></a>.</p>
<h4>Python 3.8 support dropped</h4>
<p>Support for Python 3.8 has been dropped, as it has reached its end of life.</p>
<h3>Features</h3>
<ul>
<li><em>deptry</em> now detects development dependencies from <code>[dependency-groups]</code> section, introduced by <a href="https://peps.python.org/pep-0735/">PEP 735</a> (<a href="">#892</a>)</li>
<li><em>deptry</em> now supports <code>setuptools</code> dynamic dependencies set in <code>[tool.setuptools.dynamic]</code> section, see <a href="https://deptry.com/supported-dependency-managers/#setuptools">https://deptry.com/supported-dependency-managers/#setuptools</a> for more details (<a href="">#894</a>, <a href="">#724</a>)</li>
<li>Drop support for Python 3.8 (<a href="">#874</a>)</li>
<li>Improve ignore handling (<a href="">#908</a>)</li>
<li>Parse requirements files with <code>requirements-parser</code>, adding support for parsing nested requirements files referenced with <code>-r &lt;requirement_file&gt;</code> (<a href="">#913</a>)</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/fpgmaas/deptry/compare/0.20.0...0.21.0">https://github.com/fpgmaas/deptry/compare/0.20.0...0.21.0</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/fpgmaas/deptry/blob/main/CHANGELOG.md">deptry's changelog</a>.</em></p>
<blockquote>
<h2>0.21.0 - 2024-11-08</h2>
<h3>Breaking changes</h3>
<h4>Ignore files handling</h4>
<p>Unless <a href="https://deptry.com/usage/#exclude"><code>--exclude</code></a> is used, <em>deptry</em> excludes files found in common ignore
files (<code>.gitignore</code>, <code>.ignore</code>, <code>$HOME/.config/git/ignore</code>. ...), by using <a href="https://crates.io/crates/ignore"><code>ignore</code></a>
Rust crate. The default behaviour has been changed, so that now:</p>
<ul>
<li>git-related ignore rules (<code>.gitignore</code>, <code>$HOME/.config/git/ignore</code>, ...) are only used if <em>deptry</em> is run inside a git
repository</li>
<li><code>.gitignore</code> files that are in parent directories of the git repository from where deptry is run are not
used (previously, <em>deptry</em> would traverse parent directories up to the root system)</li>
</ul>
<p>If you were using <code>.gitignore</code> files for non-git repositories, you might want to switch to <code>.ignore</code> files, or use
<a href="https://deptry.com/usage/#extend-exclude"><code>--extend-exclude</code></a>.</p>
<h4>Requirements files parsing</h4>
<p><em>deptry</em> now uses <a href="https://pypi.org/project/requirements-parser/"><code>requirements-parser</code></a> to parse dependencies from
requirements files, meaning that it can now extract nested requirements files referenced in other requirements files
without having to explicitly configure it in <em>deptry</em>.</p>
<p>For instance, if you have:</p>
<pre lang="python"><code># requirements.txt
-r cli-requirements.txt
httpx==0.27.2
</code></pre>
<pre lang="python"><code># cli-requirements.txt
click==8.1.7
</code></pre>
<p>With the default configuration, when parsing <code>requirements.txt</code>, both <code>httpx</code> and <code>click</code> will now be listed as
dependencies by <em>deptry</em>, while previously, only <code>httpx</code> was, unless <em>deptry</em> was instructed about
<code>cli-requirements.txt</code> by using <a href="https://deptry.com/usage/#requirements-files"><code>--requirements-files</code></a>. This new
behaviour also impacts development requirements files, that can be overridden by
using <a href="https://deptry.com/usage/#requirements-files-dev"><code>--requirements-files-dev</code></a>.</p>
<h4>Python 3.8 support dropped</h4>
<p>Support for Python 3.8 has been dropped, as it has reached its end of life.</p>
<h3>Features</h3>
<ul>
<li><em>deptry</em> now detects development dependencies from <code>[dependency-groups]</code> section, introduced</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>3557308</code></a> docs(changelog): add 0.21.0 release notes (<a href="">#907</a>)</li>
<li><a href=""><code>975ee16</code></a> feat(pep621): use <code>packaging</code>-based PEP 508 parser (<a href="">#925</a>)</li>
<li><a href=""><code>0781758</code></a> test(functional): remove dependency over <code>mkdocs</code> (<a href="">#935</a>)</li>
<li><a href=""><code>6a43663</code></a> test(cli): add tests for <code>display_deptry_version</code> (<a href="">#933</a>)</li>
<li><a href=""><code>18c3498</code></a> chore(deps): lock file maintenance</li>
<li><a href=""><code>28faa9a</code></a> chore(deps): update dependency mkdocs-material to v9.5.43</li>
<li><a href=""><code>ca33bb8</code></a> chore(deps): update pre-commit hook astral-sh/ruff-pre-commit to v0.7.2</li>
<li><a href=""><code>8ac81d2</code></a> chore(deps): update dependency pytest-cov to v6 (<a href="">#929</a>)</li>
<li><a href=""><code>262fe79</code></a> chore(deps): update dependency node to v22 (<a href="">#928</a>)</li>
<li><a href=""><code>9912f36</code></a> chore(renovate): update Ruff changelog URL (<a href="">#927</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/fpgmaas/deptry/compare/0.20.0...0.21.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=deptry&package-manager=pip&previous-version=0.20.0&new-version=0.21.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump deptry dependency from version 0.20.0 to 0.21.0 in pyproject.toml.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b1341953881`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.