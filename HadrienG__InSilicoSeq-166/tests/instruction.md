# Issue

**Title:** Bump joblib from 0.14.1 to 0.15.1

## Description

Bumps [joblib](https://github.com/joblib/joblib) from 0.14.1 to 0.15.1.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/joblib/joblib/blob/master/CHANGES.rst">joblib's changelog</a>.</em></p>
<blockquote>
<h1>Release 0.15.1</h1>
<ul>
<li>Make joblib work on Python 3 installation that do not ship with the lzma package in their standard library.</li>
</ul>
<h1>Release 0.15.0</h1>
<ul>
<li>Drop support for Python 2 and Python 3.5. All objects in <code>joblib.my_exceptions</code> and <code>joblib.format_stack</code> are now deprecated and will be removed in joblib 0.16. Note that no deprecation warning will be raised for these objects Python &lt; 3.7. <a href="https://github-redirect.dependabot.com/joblib/joblib/pull/1018">joblib/joblib#1018</a></li>
<li>Fix many bugs related to the temporary files and folder generated when automatically memory mapping large numpy arrays for efficient inter-process communication. In particular, this would cause PermissionError exceptions to be raised under Windows and large leaked files in /dev/shm under Linux in case of crash. <a href="https://github-redirect.dependabot.com/joblib/joblib/pull/966">joblib/joblib#966</a></li>
<li>Make the dask backend collect results as soon as they complete leading to a performance improvement: <a href="https://github-redirect.dependabot.com/joblib/joblib/pull/1025">joblib/joblib#1025</a></li>
<li>Fix the number of jobs reported by <code>effective_n_jobs</code> when <code>n_jobs=None</code> called in a parallel backend context. <a href="https://github-redirect.dependabot.com/joblib/joblib/pull/985">joblib/joblib#985</a></li>
<li>Upgraded vendored cloupickle to 1.4.1 and loky to 2.8.0. This allows for Parallel calls of dynamically defined functions with type annotations in particular.</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>60ee6fe</code></a> Release 0.15.1</li>
<li><a href=""><code>0f37803</code></a> Make LZMA optional (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1051">#1051</a>)</li>
<li><a href=""><code>4326a2f</code></a> Back to dev mode</li>
<li><a href=""><code>fea01de</code></a> Release 0.15.0 (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1049">#1049</a>)</li>
<li><a href=""><code>96bd1c4</code></a> Do not reuse temporary folders across parallel calls. (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1047">#1047</a>)</li>
<li><a href=""><code>36c06c2</code></a> Collect Dask results as they complete (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1025">#1025</a>)</li>
<li><a href=""><code>e959a01</code></a> Add a retry mechanism to the resource_tracker when unlinking memmaps (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1043">#1043</a>)</li>
<li><a href=""><code>92688c5</code></a> Removed dead code (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1027">#1027</a>)</li>
<li><a href=""><code>8a1dcdb</code></a> Use the resource_tracker to unlink shared temporary memmaps (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/966">#966</a>)</li>
<li><a href=""><code>d0a087f</code></a> bump vendored loky to v2.7.0 (<a href="https://github-redirect.dependabot.com/joblib/joblib/issues/1039">#1039</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/joblib/joblib/compare/0.14.1...0.15.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=joblib&package-manager=pip&previous-version=0.14.1&new-version=0.15.1)](https://dependabot.com/compatibility-score/?dependency-name=joblib&package-manager=pip&previous-version=0.14.1&new-version=0.15.1)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a268955ffe56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.