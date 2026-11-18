# Issue

**Title:** Update langgraph requirement from ~=0.2 to >=0.2,<2.0

## Description

[//]: # (dependabot-start)
⚠️  **Dependabot is rebasing this PR** ⚠️

Rebasing might not happen immediately, so don't worry if this takes some time.

Note: if you make any changes to this PR yourself, they will take precedence over the rebase.

---

[//]: # (dependabot-end)

Updates the requirements on [langgraph](https://github.com/langchain-ai/langgraph) to permit the latest version.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/langchain-ai/langgraph/releases">langgraph's releases</a>.</em></p>
<blockquote>
<h2>prebuilt==1.0.0</h2>
<p>Changes since prebuilt==0.7.0rc1</p>
<ul>
<li>release: langgraph + langgraph-prebuilt v1.0.0 (<a href="">#6300</a>)</li>
<li>feat: adding cursory Python 3.14 support (<a href="">#6298</a>)</li>
<li>style: fixes for ref docs (<a href="">#6297</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c4144bb</code></a> release: langgraph + langgraph-prebuilt v1.0.0 (<a href="">#6300</a>)</li>
<li><a href=""><code>2c3e380</code></a> feat: adding cursory Python 3.14 support (<a href="">#6298</a>)</li>
<li><a href=""><code>cf39fa5</code></a> fix(docs): fix catchall redirect (<a href="">#6299</a>)</li>
<li><a href=""><code>7e666b5</code></a> style: fixes for ref docs (<a href="">#6297</a>)</li>
<li><a href=""><code>3f400b3</code></a> fix(cli): install local deps in editable mode (<a href="">#6294</a>)</li>
<li><a href=""><code>6527df6</code></a> chore: release rcs for prebuilt + langgraph (<a href="">#6296</a>)</li>
<li><a href=""><code>aec841b</code></a> chore(prebuilt): un-deprecate tool node for now (<a href="">#6295</a>)</li>
<li><a href=""><code>2d3121a</code></a> chore: drop Python 3.9 (and syntax) (<a href="">#6289</a>)</li>
<li><a href=""><code>06f9142</code></a> chore(docs): Fix redirects (<a href="">#6292</a>)</li>
<li><a href=""><code>a926450</code></a> docs: Redirects for new docs (<a href="">#5824</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/langchain-ai/langgraph/compare/0.2.0...1.0.0">compare view</a></li>
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e87e78983d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.