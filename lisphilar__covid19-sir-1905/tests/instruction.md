# Issue

**Title:** build(deps): bump geopandas from 1.1.1 to 1.1.2

## Description

Bumps [geopandas](https://github.com/geopandas/geopandas) from 1.1.1 to 1.1.2.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/geopandas/geopandas/releases">geopandas's releases</a>.</em></p>
<blockquote>
<h2>Version 1.1.2</h2>
<h2>What's Changed</h2>
<p>Bug fixes:</p>
<ul>
<li>Fix an issue that caused an error in <code>GeoDataFrame.from_features</code> when there is no <code>properties</code> field (<a href="">#3599</a>).</li>
<li>Fix <code>read_file</code> and <code>to_file</code> errors (<a href="">#3682</a>)</li>
<li>Fix <code>read_parquet</code> with <code>to_pandas_kwargs</code> for complex (list/struct) arrow types (<a href="">#3640</a>)</li>
<li><code>value_counts</code> on GeoSeries now preserves CRS in index (<a href="">#3669</a>)</li>
<li>Fix f-string placeholders appearing in error messages when <code>pyogrio</code> cannot be imported (<a href="">#3682</a>).</li>
<li>Fix <code>read_parquet</code> with <code>to_pandas_kwargs</code> for complex (list/struct) arrow types (<a href="">#3640</a>).</li>
<li><code>.to_json</code> now provides a clearer error message when called on a GeoDataFrame without an active geometry
column (<a href="">#3648</a>).</li>
<li>Calling <code>del gdf[&quot;geometry&quot;]</code> now will downcast to a <code>pd.DataFrame</code> if there are no geometry columns left
in the dataframe (<a href="">#3648</a>).</li>
<li>Fix SQL injection in <code>to_postgis</code> via geometry column name (<a href="">#3681</a>).</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/geopandas/geopandas/compare/v1.1.1...v1.1.2">https://github.com/geopandas/geopandas/compare/v1.1.1...v1.1.2</a></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/geopandas/geopandas/blob/main/CHANGELOG.md">geopandas's changelog</a>.</em></p>
<blockquote>
<h2>Version 1.1.2 (December 22, 2025)</h2>
<p>Bug fixes:</p>
<ul>
<li>Fix an issue that caused an error in <code>GeoDataFrame.from_features</code> when there is no <code>properties</code> field (<a href="">#3599</a>).</li>
<li>Fix <code>read_file</code> and <code>to_file</code> errors (<a href="">#3682</a>)</li>
<li>Fix <code>read_parquet</code> with <code>to_pandas_kwargs</code> for complex (list/struct) arrow types (<a href="">#3640</a>)</li>
<li><code>value_counts</code> on GeoSeries now preserves CRS in index (<a href="">#3669</a>)</li>
<li>Fix f-string placeholders appearing in error messages when <code>pyogrio</code> cannot be imported (<a href="">#3682</a>).</li>
<li>Fix <code>read_parquet</code> with <code>to_pandas_kwargs</code> for complex (list/struct) arrow types (<a href="">#3640</a>).</li>
<li><code>.to_json</code> now provides a clearer error message when called on a GeoDataFrame without an active geometry
column (<a href="">#3648</a>).</li>
<li>Calling <code>del gdf[&quot;geometry&quot;]</code> now will downcast to a <code>pd.DataFrame</code> if there are no geometry columns left
in the dataframe (<a href="">#3648</a>).</li>
<li>Fix SQL injection in <code>to_postgis</code> via geometry column name (<a href="">#3681</a>).</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>81214bf</code></a> RLS: backport fixes for 1.1.2 (<a href="">#3693</a>)</li>
<li><a href=""><code>62dd4a2</code></a> COMPAT: pandas 3 refactor breaks <strong>finalize</strong> (<a href="">#3611</a>) (<a href="">#3621</a>)</li>
<li>See full diff in <a href="https://github.com/geopandas/geopandas/compare/v1.1.1...v1.1.2">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=geopandas&package-manager=uv&previous-version=1.1.1&new-version=1.1.2)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/lisphilar/covid19-sir/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bfb535d5e0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.