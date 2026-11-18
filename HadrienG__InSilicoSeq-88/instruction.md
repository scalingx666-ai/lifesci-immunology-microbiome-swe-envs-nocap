# Issue

**Title:** Bump joblib from 0.13.0 to 0.13.2

## Description

Bumps [joblib](https://github.com/joblib/joblib) from 0.13.0 to 0.13.2.
<details>
<summary>Changelog</summary>

*Sourced from [joblib's changelog](https://github.com/joblib/joblib/blob/master/CHANGES.rst).*

> Release 0.13.2
> ==============
>
> Pierre Glaser
>
> > Upgrade to cloudpickle 0.8.0
> >
> > Add a non-regression test related to joblib issues [\#836](https://github-redirect.dependabot.com/joblib/joblib/issues/\836) and [\#833](https://github-redirect.dependabot.com/joblib/joblib/issues/\833), reporting that cloudpickle versions between 0.5.4 and 0.7 introduced a bug where global variables changes in a parent process between two calls to joblib.Parallel would not be propagated into the workers
>
> Release 0.13.1
> ==============
>
> Pierre Glaser
>
> > Memory now accepts pathlib.Path objects as `location` parameter. Also, a warning is raised if the returned backend is None while `location` is not None.
>
> Olivier Grisel
>
> > Make `Parallel` raise an informative `RuntimeError` when the active parallel backend has zero worker.
> >
> > Make the `DaskDistributedBackend` wait for workers before trying to schedule work. This is useful in particular when the workers are provisionned dynamically but provisionning is not immediate (for instance using Kubernetes, Yarn or an HPC job queue).
</details>
<details>
<summary>Commits</summary>

-  Release 0.13.2
-  Upgrade to cloudpickle 0.8.0 ()
-  Release 0.13.1
-  [MRG] Improve error when using dask parallel backend and dask is not installe...
-  FIX explicit error when effective_n_jobs is 0 ()
-  ENH/TEST : Add test case for import errors at top level ()
-  ENH Accept pathlib path for  store backend factory ()
-  [DOC] More typos ()
-  typo memmap example ()
- See full diff in [compare view](https://github.com/joblib/joblib/compare/0.13.0...0.13.2)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=joblib&package-manager=pip&previous-version=0.13.0&new-version=0.13.2)](https://dependabot.com/compatibility-score.html?dependency-name=joblib&package-manager=pip&previous-version=0.13.0&new-version=0.13.2)

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