# Issue

**Title:** Switch the dev/CI toolchain from conda to uv

## Description

## Why

The only thing tying arda's dev environment to conda was the mmseqs2 bioconda binary. mmseqs2 ships an official **static** build, which arda already discovers and auto-fetches (`$ARDA_MMSEQS` → `bin/mmseqs` → PATH → fetch), so conda buys nothing for development.

## Changes

- **`setup.sh`** — `uv venv .venv` + `uv pip install -e . --no-build-isolation` (build deps live in the venv so the scikit-build editable on-import rebuild can find pybind11), then fetch the IgBLAST release and a static mmseqs2 (skipped when one is already on PATH). Portable under **bash and zsh** (`${BASH_SOURCE[0]:-$0}`). Flags trimmed to `--build-db` / `--tests`.
- **`.github/workflows/ci.yml`** — `astral-sh/setup-uv`, `uv pip install --system` for the toolchain and the editable install.
- **README + repo `memory/`** — conda → uv; mmseqs is the static binary, no conda.
- **Delete the root `environment.yml`** (dev conda env).

## Scope — ISP/Gamaleya integration keeps conda

Conda survives **only** in `integrations/nextflow/arda/` (the Gamaleya/ISP Nextflow pipeline), which ships its own `environment.yml` + Dockerfile. Untouched.

## Validation

Full uv install exercised locally: `.venv` builds the `_markup` C++ extension, `import arda` (2.5.6) works, mmseqs resolves off PATH with no conda / `ARDA_MMSEQS`. `bash -n` / `zsh -n` clean; `ROOT` resolves identically under both shells. Unit + synthetic + realworld suite green in the uv venv.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a203a2999dcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.