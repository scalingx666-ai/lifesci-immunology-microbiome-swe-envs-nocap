# Issue

**Title:** [Security] Bump urllib3 from 1.24.1 to 1.24.2

## Description

Bumps [urllib3](https://github.com/urllib3/urllib3) from 1.24.1 to 1.24.2. **This update includes security fixes.**
<details>
<summary>Vulnerabilities fixed</summary>

*Sourced from The GitHub Security Advisory Database.*

> **High severity vulnerability that affects urllib3**
> The urllib3 library before 1.24.2 for Python mishandles certain cases where the desired set of CA certificates is different from the OS store of CA certificates, which results in SSL connections succeeding in situations where a verification failure is the correct outcome. This is related to use of the ssl_context, ca_certs, or ca_certs_dir argument.
>
> Affected versions: < 1.24.2

</details>
<details>
<summary>Changelog</summary>

*Sourced from [urllib3's changelog](https://github.com/urllib3/urllib3/blob/master/CHANGES.rst).*

> 1.24.2 (2019-04-17)
> ===================
>
> -   Don't load system certificates by default when any other `ca_certs`, `ca_certs_dir` or `ssl_context` parameters are specified.
> -   Remove Authorization header regardless of case when redirecting to cross-site. (Issue )
> -   Add support for IPv6 addresses in subjectAltName section of certificates. (Issue )
</details>
<details>
<summary>Commits</summary>

-  Release 1.24.2 ()
- See full diff in [compare view](https://github.com/urllib3/urllib3/compare/1.24.1...1.24.2)
</details>
<br />

[![Dependabot compatibility score](https://api.dependabot.com/badges/compatibility_score?dependency-name=urllib3&package-manager=pip&previous-version=1.24.1&new-version=1.24.2)](https://dependabot.com/compatibility-score.html?dependency-name=urllib3&package-manager=pip&previous-version=1.24.1&new-version=1.24.2)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4e8bf50bda0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.