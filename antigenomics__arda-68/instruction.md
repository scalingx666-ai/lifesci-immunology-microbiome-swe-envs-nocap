# Issue

**Title:** Nextflow module + docs: pin arda-mapper 2.5.3

## Description

The module still installed **2.5.1**, whose reference builds scaffolds from 3′-truncated V alleles —
so a collaborator following the integration docs would have got junctions short by up to 3 aa on the
affected genes, **silently**. This is the delivery path for the Gamaleya/ISP integration, so the pin
matters.

Bumped: `environment.yml`, the `container` tag, the `Dockerfile` build commands, the module README,
and `docs/pipeline_integration.rst`.

## Verified against the published 2.5.3, not just bumped

- Clean venv + empty `XDG_CACHE_HOME` → auto-fetches the **v2.5.3** release asset: **16,035
  scaffolds** (2.5.2 shipped 17,668), **0 junctions not starting at Cys104** (2.5.2 shipped 570),
  `TRAV20*03` absent.
- The module run through **Nextflow 26.04.6** publishes a `clones.tsv` **identical** to the
  standalone run and to the committed `examples/rnaseq/clones.tsv`.
- `airr` emits one file, contigs land on `assembled_airr`, and `versions.yml` reports `arda: 2.5.3`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b868ccbca1b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.