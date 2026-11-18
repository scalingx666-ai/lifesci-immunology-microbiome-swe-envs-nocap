# Issue

**Title:** Bump pycodestyle from 2.5.0 to 2.6.0

## Description

Bumps [pycodestyle](https://github.com/PyCQA/pycodestyle) from 2.5.0 to 2.6.0.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/PyCQA/pycodestyle/blob/master/CHANGES.txt">pycodestyle's changelog</a>.</em></p>
<blockquote>
<h2>2.6.0 (2020-05-11)</h2>
<p>Announcements:</p>
<ul>
<li>Anthony Sottile (<a href="https://github.com/asottile">@asottile</a>) joined the team as a core developer. :tada:</li>
</ul>
<p>Changes:</p>
<ul>
<li>E306: fix detection inside <code>async def</code>.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/929">#929</a>.</li>
<li>E301: fix regression disallowing decorated one-liners.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/927">#927</a>.</li>
<li>E714: fix false positive with chained <code>is not</code>.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/931">#931</a>.</li>
</ul>
<h2>2.6.0a1 (2020-04-23)</h2>
<p>New checks:</p>
<ul>
<li>E225: require whitespace around <code>and</code> <code>in</code> <code>is</code> and <code>or</code>.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/847">#847</a>.</li>
</ul>
<p>Changes:</p>
<ul>
<li>E117: fix indentation using tabs by treating as 8-space indents.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/837">#837</a>.</li>
<li>E721: fix false positive with names containg <code>istype</code>.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/850">#850</a>.</li>
<li>E741: allow <code>l</code> as a named argument in a function call.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/853">#853</a>.</li>
<li>E302: fix false-negative with decorated functions.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/859">#859</a>.</li>
<li>W504: ellipsis (<code>...</code>) is no longer treated as a binary operator.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/875">#875</a>.</li>
<li>E402: allow <code>with</code>, <code>if</code>, <code>elif</code>, <code>else</code> to guard imports.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/834">#834</a>.</li>
<li>Add support for assignment expressions <code>:=</code> (PEP 572).  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/879">#879</a>.</li>
<li>Add support for positional-only arguments <code>/</code> (PEP 570).  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/872">#872</a>, <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/918">#918</a>.</li>
<li>Add support for python 3.8.</li>
<li>Add support for matrix multiplication operator <code>@</code> (PEP 465).  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/897">#897</a>.</li>
<li>Support visual indent for continuation lines for <code>with</code> / <code>assert</code> /
<code>raise</code>.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/912">#912</a>.</li>
<li>E302: allow two blank lines after a block of one-liners.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/913">#913</a>.</li>
<li>E302: allow two-and-fewer newlines at the top of the file.  PR <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/919">#919</a>.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>d414383</code></a> Simplified / cleaned up the Makefile to match Travis (just use tox)</li>
<li><a href=""><code>203041b</code></a> Announce Anthony as core developer, tweak release date.</li>
<li><a href=""><code>4795a0e</code></a> Added comment reminder of how to upload these days</li>
<li><a href=""><code>0f42fed</code></a> Bumped license year</li>
<li><a href=""><code>7dad684</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/933">#933</a> from asottile/2_6_0</li>
<li><a href=""><code>82b0416</code></a> 2.6.0</li>
<li><a href=""><code>1aa4c0a</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/931">#931</a> from suzil/fix/767/chained-is-not-E714</li>
<li><a href=""><code>90026af</code></a> Merge pull request <a href="https://github-redirect.dependabot.com/PyCQA/pycodestyle/issues/927">#927</a> from asottile/allow_typing_one_liners_again</li>
<li><a href=""><code>39895aa</code></a> Handle</li>
<li><a href=""><code>5230110</code></a> E714: fix chained is not</li>
<li>Additional commits viewable in <a href="https://github.com/PyCQA/pycodestyle/compare/2.5.0...2.6.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=pycodestyle&package-manager=pip&previous-version=2.5.0&new-version=2.6.0)](https://dependabot.com/compatibility-score/?dependency-name=pycodestyle&package-manager=pip&previous-version=2.5.0&new-version=2.6.0)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Pull request limits (per update run and/or open at any time)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f0f3fe2abd97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.