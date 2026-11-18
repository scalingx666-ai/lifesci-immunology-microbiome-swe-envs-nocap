# Issue

**Title:** build(deps): bump loguru from 0.7.2 to 0.7.3

## Description

Bumps [loguru](https://github.com/Delgan/loguru) from 0.7.2 to 0.7.3.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/Delgan/loguru/releases">loguru's releases</a>.</em></p>
<blockquote>
<h2>0.7.3</h2>
<ul>
<li>Fix Cython incompatibility caused by the absence of underlying stack frames, which resulted in a <code>ValueError</code> during logging (<a href="">#88</a>).</li>
<li>Fix possible <code>RuntimeError</code> when removing all handlers with <code>logger.remove()</code> due to thread-safety issue (<a href="">#1183</a>, thanks <a href="https://github.com/jeremyk"><code>@​jeremyk</code></a>).</li>
<li>Fix <code>diagnose=True</code> option of exception formatting not working as expected with Python 3.13 (<a href="">#1235</a>, thanks <a href="https://github.com/etianen"><code>@​etianen</code></a>).</li>
<li>Fix non-standard level names not fully compatible with <code>logging.Formatter()</code> (<a href="">#1231</a>, thanks <a href="https://github.com/yechielb2000"><code>@​yechielb2000</code></a>).</li>
<li>Fix inability to display a literal <code>&quot;\&quot;</code> immediately before color markups (<a href="">#988</a>).</li>
<li>Fix possible infinite recursion when an exception is raised from a <code>__repr__</code>  method decorated with <code>logger.catch()</code> (<a href="">#1044</a>).</li>
<li>Improve performance of <code>datetime</code> formatting while logging messages (<a href="">#1201</a>, thanks <a href="https://github.com/trim21"><code>@​trim21</code></a>).</li>
<li>Reduce startup time in the presence of installed but unused <code>IPython</code> third-party library (<a href="">#1001</a>, thanks <a href="https://github.com/zakstucke"><code>@​zakstucke</code></a>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/Delgan/loguru/blob/master/CHANGELOG.rst">loguru's changelog</a>.</em></p>
<blockquote>
<h1><code>0.7.3</code>_ (2024-12-06)</h1>
<ul>
<li>Fix Cython incompatibility caused by the absence of underlying stack frames, which resulted in a <code>ValueError</code> during logging (<code> &lt;</code>_).</li>
<li>Fix possible <code>RuntimeError</code> when removing all handlers with <code>logger.remove()</code> due to thread-safety issue (<code> &lt;</code><em>, thanks <code>@jeremyk &lt;https://github.com/jeremyk&gt;</code></em>).</li>
<li>Fix <code>diagnose=True</code> option of exception formatting not working as expected with Python 3.13 (<code> &lt;</code><em>, thanks <code>@etianen &lt;https://github.com/etianen&gt;</code></em>).</li>
<li>Fix non-standard level names not fully compatible with <code>logging.Formatter()</code> (<code> &lt;</code><em>, thanks <code>@yechielb2000 &lt;https://github.com/yechielb2000&gt;</code></em>).</li>
<li>Fix inability to display a literal <code>&quot;\&quot;</code> immediately before color markups (<code> &lt;</code>_).</li>
<li>Fix possible infinite recursion when an exception is raised from a <code>__repr__</code>  method decorated with <code>logger.catch()</code> (<code> &lt;</code>_).</li>
<li>Improve performance of <code>datetime</code> formatting while logging messages (<code> &lt;</code><em>, thanks <code>@trim21 &lt;https://github.com/trim21&gt;</code></em>).</li>
<li>Reduce startup time in the presence of installed but unused <code>IPython</code> third-party library (<code> &lt;</code><em>, thanks <code>@zakstucke &lt;https://github.com/zakstucke&gt;</code></em>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>ae3bfd1</code></a> Bump version to 0.7.3</li>
<li><a href=""><code>ccca356</code></a> Replace &quot;notifiers&quot; (seems unmaintained) with &quot;apprise&quot; in docs (<a href="">#1251</a>)</li>
<li><a href=""><code>a372814</code></a> Configure &quot;trusted publishing&quot; in Github workflow</li>
<li><a href=""><code>633016d</code></a> Use tox to define the &quot;release&quot; command</li>
<li><a href=""><code>ef12cbb</code></a> Convert README from RST to MD (fix PyPI packaging)</li>
<li><a href=""><code>cb3314a</code></a> Add Github action to verify packaging</li>
<li><a href=""><code>6161a13</code></a> Complete the &quot;Troubleshooting&quot; docs with more examples</li>
<li><a href=""><code>7f5001f</code></a> Simplify the example of dynamic handler level</li>
<li><a href=""><code>2e0cd7b</code></a> Move &quot;Introduction to logging&quot; docs to a new section</li>
<li><a href=""><code>72b93d1</code></a> Correct outdated instructions for reporting a vulnerability</li>
<li>Additional commits viewable in <a href="https://github.com/Delgan/loguru/compare/0.7.2...0.7.3">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=loguru&package-manager=pip&previous-version=0.7.2&new-version=0.7.3)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- Bump loguru dependency from version 0.7.2 to 0.7.3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a4a772ca7fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.