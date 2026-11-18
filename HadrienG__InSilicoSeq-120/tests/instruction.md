# Issue

**Title:** Bump joblib from 0.13.2 to 0.14.0

## Description

Bumps [joblib](https://github.com/joblib/joblib) from 0.13.2 to 0.14.0.
<details>
<summary>Changelog</summary>

*Sourced from [joblib's changelog](https://github.com/joblib/joblib/blob/master/CHANGES.rst).*

> Release 0.14.0
> ==============
>
> -   Improved the load balancing between workers to avoid stranglers caused by an excessively large batch size when the task duration is varying significantly (because of the combined use of `joblib.Parallel` and `joblib.Memory` with a partially warmed cache for instance). <https://github-redirect.dependabot.com/joblib/joblib/pull/899>
> -   Add official support for Python 3.8: fixed protocol number in Hasher and updated tests.
> -   Fix a deadlock when using the dask backend (when scattering large numpy arrays). <https://github-redirect.dependabot.com/joblib/joblib/pull/914>
> -   Warn users that they should never use joblib.load with files from untrusted sources. Fix security related API change introduced in numpy 1.6.3 that would prevent using joblib with recent numpy versions. <https://github-redirect.dependabot.com/joblib/joblib/pull/879>
> -   Upgrade to cloudpickle 1.1.1 that add supports for the upcoming Python 3.8 release among other things. <https://github-redirect.dependabot.com/joblib/joblib/pull/878>
> -   Fix semaphore availability checker to avoid spawning resource trackers on module import. <https://github-redirect.dependabot.com/joblib/joblib/pull/893>
> -   Fix the oversubscription protection to only protect against nested Parallel calls. This allows joblib to be run in background threads. <https://github-redirect.dependabot.com/joblib/joblib/pull/934>
> -   Fix ValueError (negative dimensions) when pickling large numpy arrays on Windows. <https://github-redirect.dependabot.com/joblib/joblib/pull/920>
> -   Upgrade to loky 2.6.0 that add supports for the setting environment variables in child before loading any module. <https://github-redirect.dependabot.com/joblib/joblib/pull/940>
> -   Fix the oversubscription protection for native libraries using threadpools (OpenBLAS, MKL, Blis and OpenMP runtimes). The maximal number of threads is can now be set in children using the `inner_max_num_threads` in `parallel_backend`. It defaults to `cpu_count() // n_jobs`. <https://github-redirect.dependabot.com/joblib/joblib/pull/940>
</details>
<details>
<summary>Commits</summary>

-  Release 0.14.0
-  DOC fix typo in documentation
-  ENH over-subscription mitigation + MTN vendor loky 2.6 ()
-  ENH Improve load-balancing between workers for large batch sizes. ()
-  Missing entry in changelog
-  prevent overflow when pickling large numpy arrays ()
-  Change setup.py to import setup from setuptools which supports ()
-  Upgrade to cloudpickle 1.2.2 ()
-  Fix dask scatter deadlock ()
-  ENH only protect against nested call in Parallel ()
- Additional commits viewable in [compare view](https://github.com/joblib/joblib/compare/0.13.2...0.14.0)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=joblib&package-manager=pip&previous-version=0.13.2&new-version=0.14.0)](https://dependabot.com/compatibility-score.html?dependency-name=joblib&package-manager=pip&previous-version=0.13.2&new-version=0.14.0)

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

Finally, you can contact us by mentioning @dependabot.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cf6a9ca1f2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.