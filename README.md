# scalingX/lifesci-immunology-microbiome-swe-envs-nocap

A domain-specific SWE-style RL environment dataset built from merged pull
requests of active, high-star Immunology, Infectious Disease & Microbiome open-source repositories,
generated with the Repo2RLEnv pr_diff pipeline (Harbor task format).

Part of the lifesci-* multi-domain series. Published in parallel:
- Hugging Face: https://huggingface.co/datasets/scalingX/lifesci-immunology-microbiome-swe-envs-nocap
- GitHub: https://github.com/scalingx666-ai/lifesci-immunology-microbiome-swe-envs-nocap

## At a glance

- Build: expansion (no per-repo cap expansion)
- Target repositories: 194
- Repositories with tasks: 164
- Total tasks: 6523
- Max tasks per repository: 198 (unlimited (no per-repo cap))
- Repositories with zero yield: 30 (kept in list, never faked)
- All targets: stars >= 50, pushed since 2023-01-01, not archived, noise-filtered

## Selection

Candidates came from domain GitHub topic/name/readme searches
(see selection_stats.json). Filter: active + stars >= 50 + non-archived +
non-fork + noise removed (awesome-lists / tutorials / courses / demos / etc.).
Top repositories by stars:
- guofei9987/scikit-opt (6727 stars)
- FreedomIntelligence/OpenClaw-Medical-Skills (3107 stars)
- soedinglab/MMseqs2 (2170 stars)
- torognes/vsearch (763 stars)
- voutcn/megahit (731 stars)
- ryansmcgee/seirsplus (681 stars)
- Ecogenomics/GTDBTk (631 stars)
- pallupz/covid-vaccine-booking (592 stars)
- sourmash-bio/sourmash (565 stars)
- benjjneb/dada2 (562 stars)

Star buckets: {">=1000": 3, "500-999": 9, "200-499": 45, "100-199": 62, "50-99": 93}

## What a task is

Each task rewinds a merged PR to its base commit; the agent gets the PR title/
description (leak-stripped) and must edit the repo. A weighted diff-similarity
verifier compares its patch to the merged diff. Tasks ship a self-contained
python:3.12-slim inline Dockerfile. manifest.json / registry.json are added on
Hugging Face by repo2rlenv push.

## Files

- README.md, BREADTH_NOTES.md - card + build notes
- repo_list.txt - the domain target list
- dataset_stats.json - per-repo task counts
- selection_stats.json - selection funnel + star buckets
- zero_repos.txt - informational zero-yield list

## Caveats

- validate --deep --oracle = static structure + oracle integrity only, NOT
  a real graded Harbor reward (that needs an LLM judge key).
- Running tasks needs Docker (harbor run --env docker); generation/validation/
  publishing need neither Docker nor an LLM key.
- Hardcoded provider keys found in upstream PR diffs were redacted for public
  release. Licenses follow each source repository; generated with Repo2RLEnv.

## Snapshot scope

This release is a **partial snapshot** of an unfinished generation run.

- Generation-complete flag: generation_complete_expansion.flag - **ABSENT** (not faked)
- Bank progress at snapshot: **53477 / 100000** tasks (53.5%)
- This domain: **6523** tasks from **164** repositories

See PARTIAL_SNAPSHOT.md for the full statement.
