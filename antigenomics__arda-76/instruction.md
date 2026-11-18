# Issue

**Title:** nf: derive --organism from params.genome, gate ARDA on supported assemblies

## Description

.

@EgorGuga requested that the Nextflow module's `nextflow.config`:
1. run ARDA only when `params.genome` is `GRCh38` or `GRCm39`, and
2. set `--organism` to `human` / `mouse` from the assembly.

The module's `main.nf` already honours both hooks this needs — `task.ext.when` (its `when:` block) and `task.ext.args` — so the change is entirely in the config, no module edit:

```groovy
ext.when = { params.genome in ['GRCh38', 'GRCm39'] }
ext.args = {
    params.genome == 'GRCh38' ? '--organism human' :
    params.genome == 'GRCm39' ? '--organism mouse' : ''
}
```

`params.genome` is the iGenomes key nf-core sets from `--genome`, so ARDA follows whatever assembly the rest of the pipeline is already running on — nothing extra to configure. Any other genome (or none) skips ARDA and the pipeline still completes.

### Verified end-to-end (not just parsed)

On aldan3 with real Nextflow (21.10.6), the **real module + this config**, and a fake `arda` on PATH that records its argv:

| `--genome` | ARDA runs? | `--organism` received |
|---|---|---|
| `GRCh38` | ✅ | `human` |
| `GRCm39` | ✅ | `mouse` |
| `GRCh37` | skipped | — |
| *(unset)* | skipped | — |

The skipped cases complete with no error; the two supported cases publish all four output files.

Docs updated (module `README.md` + `pipeline_integration.rst`): the genome→organism mapping, and that a static `ext.args` string overrides the genome-driven default. Sphinx `-W` build clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44cd6a9aa7be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.