# Issue

**Title:** Honour compress_grids: write ASCII grids gzipped as .asc.gz

## Description

## Summary

`compress_grids = True` has never done anything in Circuitscape.jl. The option was parsed and passed around, but it never reached the writer, so maps were always written as plain `.asc`. The options reference says it "compresses output ASCII grids using gzip", which is what Circuitscape 4 did.

- `write_grid` now passes `cfg.compress_grids` to `write_raster`.
- `write_raster` and `write_asc` take a new `compress` keyword (default `false`). With it set, each map is written as `<name>.asc.gz` through GZip.jl, which is already a dependency. The `.prj` sidecar is still `<name>.prj`, which is where the reader looks for it.
- GeoTIFF output (`write_as_tif = True`) is unchanged; it is always LZW-compressed.
- Reading `.asc.gz` input already worked.

**User-visible change:** an INI file that sets `compress_grids = True` now produces `.asc.gz` maps instead of `.asc`. This is noted in the migration guide. One fixture sets it (`advanced/7/mgVerify7.ini`), but no test runs that fixture.

On a 1500×1500 grid, writing gzipped takes 0.69 s against 0.24 s for plain text, and the file is 18.7 MiB against 39.0 MiB. Writing `writedlm` output straight into the GZip stream is as fast as buffering it first.

Docs: the `compress_grids` row in the options reference said output was "currently written uncompressed". It now describes the option, and the *Compress Output Grids* section names the `.asc.gz` files.

## Test plan

- [x] New `compress_grids` testset runs a pairwise job with current and voltage maps twice, once plain and once compressed. Resistances match, every map comes out as `.asc.gz` with the gzip magic bytes, and each one reads back equal to its plain counterpart.
- [x] The ASCII grid I/O test now writes its gzipped fixture with `write_raster(...; compress = true)` instead of calling GZip directly. It checks that the grid, projection and transform round-trip.
- [x] `Pkg.test()` passes locally: 1468 unit tests plus the cg+amg and cholmod runs. Apple Accelerate, Pardiso and AMGX were skipped because they aren't available on this machine.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `676139797e8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.