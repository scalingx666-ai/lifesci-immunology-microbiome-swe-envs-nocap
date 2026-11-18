# Build notes - Immunology, Infectious Disease & Microbiome

Repo2RLEnv pr_diff (v0.9.6), Harbor-format output. Domain: immunology-microbiome.

## Funnel

| Stage | Count |
|---|---|
| Domain candidates (deduped) | 414 |
| After active+star+noise filter | 212 |
| Final target list (cap unlimited) | 212 |
| Repos with >=1 task | 164 |
| Repos with 0 tasks | 30 |
| Total tasks (unlimited (no per-repo cap)) | 6523 |

## Generation

- Shared task bank: each repo generated once (pr_diff, limit=3,
  max_files_per_pr=15, min_loc_changed=2), 4-way concurrency,
  rate-limit-aware with .done checkpoint resume.
- Per-domain consolidation: rank by reward_calibration.loc_changed desc,
  keep ALL qualifying tasks (no per-repo cap). Zero-yield repos are NOT fabricated.
- Overlap with the 3 published cancer editions is allowed (user decision);
  domains are independent selections, not a partition of one repo set.

## Zero-yield repos (informational, 30)

- taowenmicro/EasyMicrobiomeR
- GenerTeam/GENERanno
- GaetanBenoitDev/metaMDBG
- PKU-EMBL/BASALT
- CSSEGISandData/COVID-19_Unified-Dataset
- antigenomics/vdjdb-db
- MaximilianKohler/HumanMicrobiome
- dreji18/Bio-Epidemiology-NER
- xia-lab/MicrobiomeAnalystR
- mims-harvard/COMPASS
- msberends/AMR
- taowenmicro/EasyMultiOmics
- styczynski/bioseqdb
- EMOD-Hub/EMOD
- Trhova/Multi-omics
- ibe-uw/tiara
- donovan-h-parks/STAMP
- borenstein-lab/microbiome-metabolome-curated-data
- rrwick/Metagenomics-Index-Correction
- Merck/Sapiens
- songweizhi/MetaCHIP
- lmrodriguezr/nonpareil
- HUST-NingKang-Lab/MGM
- iquasere/KEGGCharter
- P-kai/EasyNanoMeta
- instadeepai/FrameDiPT
- pengxingang/TEIM
- xuechunxu/DiTing
- flowhub-team/Metagenomics
- yuezhengfu/CNPS.cycle

## Caveats

- Static validation only; real grading needs an LLM judge key + Docker.
- inline_dockerfile mode skips image build (no Docker daemon needed to publish).
- Provider secrets in upstream diffs were redacted before public release.
