# Issue

**Title:** Bump pycodestyle from 2.4.0 to 2.5.0

## Description

Bumps [pycodestyle](https://github.com/PyCQA/pycodestyle) from 2.4.0 to 2.5.0.
<details>
<summary>Changelog</summary>

*Sourced from [pycodestyle's changelog](https://github.com/PyCQA/pycodestyle/blob/master/CHANGES.txt).*

> 2.5.0 (2019-01-29)
> ------------------
>
> New checks:
>
> * E117: Over-indented code blocks
> * W505: Maximum doc-string length only when configured with --max-doc-length
>
> Changes:
>
> * Remove support for EOL Python 2.6 and 3.3. PR .
> * Add E117 error for over-indented code blocks.
> * Allow W605 to be silenced by `# noqa` and fix the position reported by W605
> * Allow users to omit blank lines around one-liner definitions of classes and
>   functions
> * Include the function return annotation (``->``) as requiring surrounding
>   whitespace only on Python 3
> * Verify that only names can follow ``await``. Previously we allowed numbers
>   and strings.
> * Add support for Python 3.7
> * Fix detection of annotated argument defaults for E252
> * Cprrect the position reported by W504
</details>
<details>
<summary>Commits</summary>

-  Add release notes for 2.5.0
-  Merge pull request  from asottile/noqa_W605
-  Allow W605 to be silenced by noqa
-  Merge pull request  from jdufresne/over-indented
-  Merge pull request  from jdufresne/xenial
-  Use 'dist: xenial' in Travis to simplify configuration
-  Add check for over-indented blocks
-  Merge pull request  from anntzer/allow-no-blanks-around-one-liners
-  Merge pull request  from wwwjfy/issue-811
-  Merge pull request  from jdufresne/rst
- Additional commits viewable in [compare view](https://github.com/PyCQA/pycodestyle/compare/2.4.0...2.5.0)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=pycodestyle&package-manager=pip&previous-version=2.4.0&new-version=2.5.0)](https://dependabot.com/compatibility-score.html?dependency-name=pycodestyle&package-manager=pip&previous-version=2.4.0&new-version=2.5.0)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

**Note:** This repo was added to Dependabot recently, so you'll receive a maximum of 5 PRs for your first few update runs. Once an update run creates fewer than 5 PRs we'll remove that limit.

You can always request more updates by clicking `Bump now` in your [Dependabot dashboard](https://app.dependabot.com).

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot ignore this [patch|minor|major] version` will close this PR and stop Dependabot creating any more for this minor/major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)
- `@dependabot use these labels` will set the current labels as the default for future PRs for this repo and language
- `@dependabot use these reviewers` will set the current reviewers as the default for future PRs for this repo and language
- `@dependabot use these assignees` will set the current assignees as the default for future PRs for this repo and language
- `@dependabot use this milestone` will set the current milestone as the default for future PRs for this repo and language
- `@dependabot badge me` will comment on this PR with code to add a "Dependabot enabled" badge to your readme

Additionally, you can set the following in your Dependabot [dashboard](https://app.dependabot.com):
- Update frequency (including time of day and day of week)
- Automerge options (never/patch/minor, and dev/runtime dependencies)
- Pull request limits (per update run and/or open at any time)
- Out-of-range updates (receive only lockfile updates, if desired)
- Security updates (receive only security updates, if desired)

Finally, you can contact us by mentioning @dependabot.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `176162474a84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.