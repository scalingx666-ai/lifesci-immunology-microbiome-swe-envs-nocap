# Issue

**Title:** Read and write ESRI ASCII grids natively, without GDAL or a lock

## Description

First of two PRs; the second makes ArchGDAL a weak dependency and re-architects CI around it.

## Before
Every raster read and every map write went through ArchGDAL: `.asc` files were parsed by the AAIGrid driver, and written via a MEM dataset + `CreateCopy` under `IO_LOCK` (GDAL is not thread-safe). `IO_LOCK` exists for nothing else, so on a parallel pairwise run with `write_cur_maps = True` every map write was serialized on the critical path.

## After
- **`read_asc`** handles the header dialects GDAL accepts — `xllcorner`/`yllcorner` or `xllcenter`/`yllcenter`, `cellsize` or `dx`/`dy`, optional `NODATA_value`, any case, gzipped — and parses the body line by line. The line-by-line parser is not a stylistic choice: the shipped fixtures mix tabs, runs of spaces, trailing delimiters and CRLF, which trips `readdlm`'s delimiter auto-detection (`missing value at row 1 column 6` on a trailing tab). It also reports row/column count mismatches by file and line. A `.prj` sidecar supplies the WKT.
- **`write_asc`**: header + `writedlm`, no lock; a `.prj` sidecar is written when the input carried a projection, as the AAIGrid driver does. Emits `dx`/`dy` for non-square cells.
- `read_raster`/`write_raster` dispatch on format: `.asc` native, everything else (`.tif`, `.tif.gz`) through the unchanged GDAL code, now in `read_raster_gdal`/`write_raster_gdal`, which is the only place `IO_LOCK` remains.

## Measured (single thread, best of 3, `rand(n,n) .* 100`)
| `.asc` | GDAL write | native write | GDAL read | native read |
|---|---|---|---|---|
| 10 MB (750²) | 0.23 s | **0.06 s** | 0.04 s | 0.04 s |
| 100 MB (2400²) | 2.20 s | **0.58 s** | 0.40 s | 0.44 s |

Writing is 3.8× faster and files are ~17% smaller (GDAL emits more digits than round-trip needs). **Reading is parity** — within noise of GDAL at both sizes — so the read-side motivation is independence from GDAL and exactness, not speed.

## A finding
The native reader is *more* accurate than GDAL on the existing fixtures: the AAIGrid driver stores several of them as Float32 (`2.002` → `2.0020000934`), the native parser gives the exact double. The equivalence test below therefore compares at Float32 tolerance.

## Tests
Round trip with/without projection; center-origin, `dx`/`dy`, no-`NODATA`, tab, CRLF and mixed-case headers; custom nodata and NaN → -9999; single-row grid; `.asc.gz`; header/body mismatch error. Plus a sweep: every one of the 133 `.asc` fixtures reads the same natively as through GDAL (array at Float32 tolerance, transform, WKT). Full suite passes: all solver/precision runs 719/719.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78510279411d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.