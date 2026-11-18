# Issue

**Title:** Make ArchGDAL an optional package extension; run each extension once in CI

## Description

Stacked on #492; retarget to master once it lands.

## Why
With `.asc` handled natively (#492), GDAL is needed only for GeoTIFF input and `write_as_tif` output — yet it is the single heaviest thing in the install: ArchGDAL pulls GDAL, PROJ, GEOS, HDF5, NetCDF, Arrow, libgeotiff, SQLite, LibPQ and friends. Measured on this branch: the default install resolves **110 packages without ArchGDAL versus 195 with it** — the extension removes 85 packages, essentially all of them binary artifacts, plus their precompile time.

## What
- `ArchGDAL` moves to `[weakdeps]`; `read_raster_gdal`/`write_raster_gdal` move verbatim into `ext/CircuitscapeArchGDALExt.jl`, **together with `IO_LOCK`**, which now guards only GDAL calls. The core keeps fallback methods that error with the fix (`Pkg.add("ArchGDAL")`, `using ArchGDAL`); the extension's methods are strictly more specific, so nothing is overwritten.
- **Fail fast**: `validate(cfg)` checks up front, when the extension is not loaded, whether any configured raster is a GeoTIFF (by content — TIFF magic — not extension, so text lists with odd names are unaffected) or `write_as_tif = True`, and reports it with the other configuration problems before any data is read.
- Docs: a *GeoTIFF Support* section in `compute.md` mirroring Pardiso/Accelerate, the `habitat_file`/`write_as_tif` rows in `options.md`, and a README note.

## CI re-architecture
| job | platforms | loads | tests |
|---|---|---|---|
| **core** (fast path) | ubuntu, windows, ubuntu/min | nothing extra; `julia-runtest` | CG+AMG, CHOLMOD × Float64/Float32, native `.asc`; GeoTIFF fixtures skipped |
| **core + Pardiso, GDAL** | ubuntu | `Pkg.add(["Pardiso","ArchGDAL"])` | everything, incl. Pardiso and the GeoTIFF fixtures |
| **core + Accelerate, GDAL** | macOS | `Pkg.add(["AppleAccelerate","ArchGDAL"])` | everything, incl. Accelerate ×2 precisions and GeoTIFF |

Each weak dependency is exercised exactly once; no platform runs the suite twice (macOS runs only the extension job). Five jobs, as before. The test harness decides per case: `requires_gdal(ini)` sniffs the configured rasters, and `@gdal_or_skip` skips the case with a log line when ArchGDAL is absent.

## Verified locally
- **Without ArchGDAL** (110 packages resolved): every suite 685/719 (the 34 GeoTIFF cases skipped, announced), Unit 78/78; the validate test confirms a `.tif` polygon file and `write_as_tif` are refused with the install hint.
- **With ArchGDAL + AppleAccelerate**: every suite 719/719 — CG+AMG, CHOLMOD, Accelerate × Float64/Float32 — Unit 210/210 (includes the 133-file native-vs-GDAL sweep).

## Compatibility
Breaking for users reading GeoTIFF without `using ArchGDAL`: they now get an actionable error instead of a result. If 6.0.0 is not yet registered this can ride along; otherwise it is 7.0.0. Omniscape loads ArchGDAL itself and is unaffected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d77cc1502d2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.