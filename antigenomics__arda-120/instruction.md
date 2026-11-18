# Issue

**Title:** build: pybind11 → nanobind>=2.5

## Description

All four C++ extensions (`_markup`, `_prefilter`, `_segmap`, `_denoise` — 1,678 lines) now build against `nanobind>=2.5,<3`.

Your call, not a performance one, and the measurement that says so still stands: nanobind's ceiling on `transfer_regions` is **~0.15 % end-to-end** (benchmark repo, round 18). Measured on the port itself — the full suite is **1,120 passed / 9 skipped either way**, and a wheel built from scratch installs and imports all four in a clean venv.

## The port produced exactly two compile errors

Both `.def_property_readonly` → `.def_prop_ro`. The other three rules are mechanical:

| pybind11 | nanobind |
|---|---|
| `py::error_already_set` | `nb::python_error` |
| `py::reinterpret_steal` / `_borrow` | `nb::steal` / `nb::borrow` |
| `.def_property_readonly` | `.def_prop_ro` |
| `<pybind11/stl.h>` | **one header per STL type** |

The last one is the trap: a missing `nanobind/stl/<type>.h` is a **runtime conversion failure**, not a compile error. All seven are included (`string`, `vector`, `tuple`, `pair`, `map`, `unordered_map`, `optional`) and the suite is what proves they're wired — plus a direct check of every `def_prop_ro` property and the tuple/vector returns.

## One thing that cost a build cycle

`Interpreter` is **not** optional in `find_package(Python COMPONENTS ...)`. Dropping it looks right (we generate no stubs) and nanobind's own config refuses without it. Recorded as a `Never:` in `CLAUDE.md`.

## Also updated

`setup.sh`, both CI workflows, `docs/installation.rst`, `CLAUDE.md` (with the porting notes for the next one), and the `dev` extra.

Goes out as its own release rather than riding 2.26.0 — it's a build/ABI change and deserves its own version.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f4084a7348a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.