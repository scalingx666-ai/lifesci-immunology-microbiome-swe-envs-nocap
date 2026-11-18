# Issue

**Title:** build(deps): bump geopandas from 1.0.1 to 1.1.1

## Description

Bumps [geopandas](https://github.com/geopandas/geopandas) from 1.0.1 to 1.1.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/geopandas/geopandas/releases">geopandas's releases</a>.</em></p>
<blockquote>
<h2>v1.1.1</h2>
<p>A patch release containing minor regression fixes.</p>
<h2>What's Changed</h2>
<ul>
<li>REGR: fix GeoDataFrame constructor when np.nan given as only geometry by <a href="https://github.com/martinfleis"><code>@​martinfleis</code></a> in <a href="">geopandas/geopandas#3591</a></li>
<li>REGR: overlay with identity doesn't handle equal input column names correctly by <a href="https://github.com/theroggy"><code>@​theroggy</code></a> in <a href="">geopandas/geopandas#3596</a></li>
<li>TST: use nadgrids=null to suppress influence of grid files by <a href="https://github.com/mwtoews"><code>@​mwtoews</code></a> in <a href="">geopandas/geopandas#3588</a></li>
<li>MAINT: enable pydocstyle ruff rules - automatic and easy fixes by <a href="https://github.com/theroggy"><code>@​theroggy</code></a> in <a href="">geopandas/geopandas#3598</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/geopandas/geopandas/compare/v1.1.0...v1.1.1">https://github.com/geopandas/geopandas/compare/v1.1.0...v1.1.1</a></p>
<h2>v1.1.0</h2>
<p>Notes on dependencies:</p>
<ul>
<li>GeoPandas 1.1 now requires Python 3.10 or greater and pandas 2.0, numpy 1.24, pyproj 3.5,
are now the minimum required version for these dependencies.
Furthermore, the minimum tested version for optional dependencies has been updated to
fiona 1.8.21, scipy 1.9, matplotlib 3.7, mapclassify 2.5, folium 0.12 and
SQLAlchemy 2.0. Older versions of these libraries may continue to work, but are no longer
considered supported (<a href="">#3371</a>).</li>
</ul>
<p>New features and improvements:</p>
<ul>
<li>Added options to return the result of <code>SpatialIndex.query</code> in a form of a dense or a
sparse boolean array. This adds optional dependency on <code>scipy</code> for the sparse output.
Note that this also changes the previously undocumented behaviour of the <code>output_format</code>
keyword (<a href="">#1674</a>).</li>
<li>Add <code>grid_size</code> parameter to <code>union_all</code> and <code>dissolve</code> (<a href="">#3445</a>).</li>
<li><code>GeoDataFrame.plot</code> now supports <code>pd.Index</code> as an input for the <code>column</code> keyword (<a href="">#3463</a>).</li>
<li>Added <code>disjoint_subset</code> union algorithm for <code>union_all</code> and <code>dissolve</code> (<a href="">#3534</a>).</li>
<li>Added <code>constrained_delaunay_triangles</code> method to GeoSeries/GeoDataFrame (<a href="">#3552</a>).</li>
<li>Added <code>to_pandas_kwargs</code> argument to <code>from_arrow</code>, <code>read_parquet</code> and <code>read_feather</code>
to allow better control of conversion of non-geometric Arrow data to DataFrames (<a href="">#3466</a>).</li>
<li>Added <code>is_valid_coverage</code> and <code>invalid_coverage_edges</code> to GeoSeries/GeoDataFrame to
allow validation of polygonal  coverage (<a href="">#3545</a>).</li>
<li>Added <code>maximum_inscribed_circle</code> method from shapely to GeoSeries/GeoDataFrame (<a href="">#3544</a>).</li>
<li>Added <code>minimum_clearance_line</code> method from shapely to GeoSeries/GeoDataFrame (<a href="">#3543</a>).</li>
<li>Added <code>orient_polygons</code> method from shapely to GeoSeries/GeoDataFrame (<a href="">#3559</a>).</li>
<li>Added <code>method</code> and <code>keep_collapsed</code> argument to <code>make_valid</code> (<a href="">#3548</a>).</li>
<li>Added <code>simplify_coverage</code> method for topological simplification of polygonal coverages
to GeoSeries/GeoDataFrame (<a href="">#3541</a>).</li>
<li>Added initial support of M coordinates (<code>m</code> and <code>has_m</code> properties, <code>include_m</code> in <code>get_coordinates</code>) (<a href="">#3561</a>).</li>
<li>Added <code>geom_equals_identical</code> method exposing <code>equals_identical</code> from shapely to GeoSeries/GeoDataFrame (<a href="">#3560</a>).</li>
<li>GeoPandas now attempts to use a range request when reading from an URL even if the header
does not directly indicate its support (<a href="">#3572</a>).</li>
<li>Added <code>geopandas.accessors</code> module. Import this module to register a
<code>pandas.Series.geo</code> accessor, which exposes GeoSeries methods via pandas's
extension mechanism (<a href="">#3272</a>).</li>
<li>Improve performance of <code>overlay</code> with <code>how=identity</code> (<a href="">#3504</a>).</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/geopandas/geopandas/blob/main/CHANGELOG.md">geopandas's changelog</a>.</em></p>
<blockquote>
<h2>Version 1.1.1 (June 27, 2025)</h2>
<p>Bug fixes:</p>
<ul>
<li>Fix regression in the GeoDataFrame constructor when np.nan is given as an only geometry (<a href="">#3591</a>).</li>
<li>Fix regression in <code>overlay</code> with <code>how=&quot;identity&quot;</code> when input dataframes have column
names that are equal (<a href="">#3596</a>).</li>
</ul>
<h2>Version 1.1.0 (June 1, 2025)</h2>
<p>Notes on dependencies:</p>
<ul>
<li>GeoPandas 1.1 now requires Python 3.10 or greater and pandas 2.0, numpy 1.24, pyproj 3.5,
are now the minimum required version for these dependencies.
Furthermore, the minimum tested version for optional dependencies has been updated to
fiona 1.8.21, scipy 1.9, matplotlib 3.7, mapclassify 2.5, folium 0.12 and
SQLAlchemy 2.0. Older versions of these libraries may continue to work, but are no longer
considered supported (<a href="">#3371</a>).</li>
</ul>
<p>New features and improvements:</p>
<ul>
<li>Added options to return the result of <code>SpatialIndex.query</code> in a form of a dense or a
sparse boolean array. This adds optional dependency on <code>scipy</code> for the sparse output.
Note that this also changes the previously undocumented behaviour of the <code>output_format</code>
keyword (<a href="">#1674</a>).</li>
<li>Add <code>grid_size</code> parameter to <code>union_all</code> and <code>dissolve</code> (<a href="">#3445</a>).</li>
<li><code>GeoDataFrame.plot</code> now supports <code>pd.Index</code> as an input for the <code>column</code> keyword (<a href="">#3463</a>).</li>
<li>Added <code>disjoint_subset</code> union algorithm for <code>union_all</code> and <code>dissolve</code> (<a href="">#3534</a>).</li>
<li>Added <code>constrained_delaunay_triangles</code> method to GeoSeries/GeoDataFrame (<a href="">#3552</a>).</li>
<li>Added <code>to_pandas_kwargs</code> argument to <code>from_arrow</code>, <code>read_parquet</code> and <code>read_feather</code>
to allow better control of conversion of non-geometric Arrow data to DataFrames (<a href="">#3466</a>).</li>
<li>Added <code>is_valid_coverage</code> and <code>invalid_coverage_edges</code> to GeoSeries/GeoDataFrame to
allow validation of polygonal  coverage (<a href="">#3545</a>).</li>
<li>Added <code>maximum_inscribed_circle</code> method from shapely to GeoSeries/GeoDataFrame (<a href="">#3544</a>).</li>
<li>Added <code>minimum_clearance_line</code> method from shapely to GeoSeries/GeoDataFrame (<a href="">#3543</a>).</li>
<li>Added <code>orient_polygons</code> method from shapely to GeoSeries/GeoDataFrame (<a href="">#3559</a>).</li>
<li>Added <code>method</code> and <code>keep_collapsed</code> argument to <code>make_valid</code> (<a href="">#3548</a>).</li>
<li>Added <code>simplify_coverage</code> method for topological simplification of polygonal coverages
to GeoSeries/GeoDataFrame (<a href="">#3541</a>).</li>
<li>Added initial support of M coordinates (<code>m</code> and <code>has_m</code> properties, <code>include_m</code> in <code>get_coordinates</code>) (<a href="">#3561</a>).</li>
<li>Added <code>geom_equals_identical</code> method exposing <code>equals_identical</code> from shapely to GeoSeries/GeoDataFrame (<a href="">#3560</a>).</li>
<li>GeoPandas now attempts to use a range request when reading from an URL even if the header
does not directly indicate its support (<a href="">#3572</a>).</li>
<li>Added <code>geopandas.accessors</code> module. Import this module to register a
<code>pandas.Series.geo</code> accessor, which exposes GeoSeries methods via pandas's
extension mechanism (<a href="">#3272</a>).</li>
<li>Improve performance of <code>overlay</code> with <code>how=identity</code> (<a href="">#3504</a>).</li>
<li>A warning message is raised in <code>read_file</code> when a GeoDataFrame or GeoSeries mask
and/or the source dataset is missing a defined CRS (<a href="">#3464</a>).</li>
<li>GeoDataFrame no longer hard-codes the class internally, allowing easier subclassing (<a href="">#3505</a>).</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>e9b58ce</code></a> RLS: v1.1.1</li>
<li><a href=""><code>c6bf8b3</code></a> MAINT: enable pydocstyle ruff rules - automatic and easy fixes (<a href="">#3598</a>)</li>
<li><a href=""><code>339c7f7</code></a> TST: use nadgrids=null to suppress influence of grid files (<a href="">#3588</a>)</li>
<li><a href=""><code>2a7fad9</code></a> REGR: overlay with identity doesn't handle equal input column names correctly...</li>
<li><a href=""><code>1a1585d</code></a> REGR: fix GeoDataFrame constructor when np.nan given as only geometry (<a href="">#3591</a>)</li>
<li><a href=""><code>c36eba0</code></a> RSL: changelog for 1.1.0 release (<a href="">#3586</a>)</li>
<li><a href=""><code>2d6b332</code></a> remove remote url xfail (<a href="">#3585</a>)</li>
<li><a href=""><code>ce86559</code></a> DOC: Drafted new documentation page outlining how to create inset maps and in...</li>
<li><a href=""><code>d0ffe06</code></a> ENH: add error message when reading dataset without crs with a GeoDataFrame o...</li>
<li><a href=""><code>f3f145f</code></a> CI: xfail remote url test for now (<a href="">#3584</a>)</li>
<li>Additional commits viewable in <a href="https://github.com/geopandas/geopandas/compare/v1.0.1...v1.1.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=geopandas&package-manager=pip&previous-version=1.0.1&new-version=1.1.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4887b2a829f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.