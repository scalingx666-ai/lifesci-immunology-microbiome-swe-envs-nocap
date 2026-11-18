# Issue

**Title:** Bump joblib from 0.14.0 to 0.14.1

## Description

Bumps [joblib](https://github.com/joblib/joblib) from 0.14.0 to 0.14.1.
<details>
<summary>Changelog</summary>

*Sourced from [joblib's changelog](https://github.com/joblib/joblib/blob/master/CHANGES.rst).*

> Release 0.14.1
> ==============
>
> -   Configure the loky workers' environment to mitigate oversubsription with nested multi-threaded code in the following case:
>
>     -   allow for a suitable number of threads for numba (`NUMBA_NUM_THREADS`);
>     -   enable Interprocess Communication for scheduler coordination when the nested code uses Threading Building Blocks (TBB) (`ENABLE_IPC=1`)
>
>     <https://github-redirect.dependabot.com/joblib/joblib/pull/951>
>
> -   Fix a regression where the loky backend was not reusing previously spawned workers. <https://github-redirect.dependabot.com/joblib/joblib/pull/968>
> -   Revert <https://github-redirect.dependabot.com/joblib/joblib/pull/847> to avoid using pkg\_resources that introduced a performance regression under Windows: <https://github-redirect.dependabot.com/joblib/joblib/issues/965>
</details>
<details>
<summary>Commits</summary>

-  Release 0.14.1
-  Revert pkg resources ()
-  Typo
-  FIX loky workers not reused for multiple Parallel calls ()
-  CI failing fixes (sklearn doctests and joblib.hash on windows) ()
-  Fix a few typos in the docs (parallel.rst) ()
-  Clean-up left-over: TBB_NUM_THREADS is not a valid way to configure TBB
-  FIX try to make test_weak_array_key_map unlikely to fail at random ()
-  [MRG] Protect against oversubscription with numba prange / or TBB linked nati...
-  DOC minor update about prefer parameter ()
- Additional commits viewable in [compare view](https://github.com/joblib/joblib/compare/0.14.0...0.14.1)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=joblib&package-manager=pip&previous-version=0.14.0&new-version=0.14.1)](https://dependabot.com/compatibility-score.html?dependency-name=joblib&package-manager=pip&previous-version=0.14.0&new-version=0.14.1)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `681ee9625efa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.