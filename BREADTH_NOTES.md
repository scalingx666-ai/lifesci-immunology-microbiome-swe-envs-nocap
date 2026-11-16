# Build notes - Immunology, Infectious Disease & Microbiome

Repo2RLEnv pr_diff (v0.9.6), Harbor-format output. Domain: immunology-microbiome.

## Funnel

| Stage | Count |
|---|---|
| Domain candidates (deduped) | 414 |
| After active+star+noise filter | 212 |
| Final target list (cap unlimited) | 212 |
| Repos with >=1 task | 4 |
| Repos with 0 tasks | 190 |
| Total tasks (unlimited (no per-repo cap)) | 186 |

## Generation

- Shared task bank: each repo generated once (pr_diff, limit=3,
  max_files_per_pr=15, min_loc_changed=2), 4-way concurrency,
  rate-limit-aware with .done checkpoint resume.
- Per-domain consolidation: rank by reward_calibration.loc_changed desc,
  keep ALL qualifying tasks (no per-repo cap). Zero-yield repos are NOT fabricated.
- Overlap with the 3 published cancer editions is allowed (user decision);
  domains are independent selections, not a partition of one repo set.

## Zero-yield repos (informational, 190)

- guofei9987/scikit-opt
- soedinglab/MMseqs2
- torognes/vsearch
- voutcn/megahit
- ryansmcgee/seirsplus
- Ecogenomics/GTDBTk
- pallupz/covid-vaccine-booking
- sourmash-bio/sourmash
- benjjneb/dada2
- merenlab/anvio
- bxlab/metaWRAP
- fbreitwieser/pavian
- arpcard/rgi
- biobakery/MetaPhlAn
- wwood/CoverM
- metagenome-atlas/atlas
- theislab/ehrapy
- taowenmicro/EasyMicrobiomeR
- MrOlm/drep
- jenniferlu717/Bracken
- BortonWrightonLabs/DRAM
- immunomind/immunarch
- RasmussenLab/vamb
- bluenote-1577/sylph
- nf-core/mag
- GenerTeam/GENERanno
- microbiome/microbiome
- DataForScience/Epidemiology101
- bioinformatics-centre/kaiju
- ChiLiubio/microeco
- starsimhub/covasim
- EpiModel/EpiModel
- DaehwanKimLab/centrifuge
- bluenote-1577/skani
- Merck/BioPhi
- nf-core/ampliseq
- fbreitwieser/krakenuniq
- GaetanBenoitDev/metaMDBG
- gbouras13/pharokka
- CAMI-challenge/CAMISIM
- whitews/FlowKit
- COVID-19-electronic-health-system/Corona-tracker
- ratschlab/metagraph
- HadrienG/InSilicoSeq
- PKU-EMBL/BASALT
- ropensci/biomartr
- shenwei356/kmcp
- nf-core/eager
- soedinglab/metaeuk
- CodeForPhilly/chime
- PacificBiosciences/pb-metagenomics-tools
- yiluheihei/microbiomeMarker
- wwood/singlem
- YuLab-SMU/MicrobiotaProcess
- nf-core/taxprofiler
- CSSEGISandData/COVID-19_Unified-Dataset
- steineggerlab/Metabuli
- oxpig/AntiFold
- sunbeam-labs/sunbeam
- benjjneb/decontam
- nf-core/viralrecon
- dnbaker/dashing
- waldronlab/curatedMetagenomicData
- pzivich/zEpid
- biobakery/Maaslin2
- YongxinLiu/EasyMicrobiome
- antigenomics/vdjdb-db
- biobakery/kneaddata
- MaximilianKohler/HumanMicrobiome
- EBI-Metagenomics/emg-viral-pipeline
- ngless-toolkit/ngless
- torognes/swarm
- Circuitscape/Circuitscape.jl
- antigenomics/vdjtools
- eric9n/Kun-peng
- FrederickHuangLin/ANCOMBC
- lindbrook/cholera
- BioDynaMo/biodynamo
- qiita-spots/qiita
- dreji18/Bio-Epidemiology-NER
- snayfach/MIDAS
- xia-lab/MicrobiomeAnalystR
- david-barnett/microViz
- mims-harvard/COMPASS
- EBI-Metagenomics/mobilome-annotation-pipeline
- rhysnewell/aviary
- spacegraphcats/spacegraphcats
- greenelab/covid19-review
- nf-core/funcscan
- msberends/AMR
- EBI-Metagenomics/genomes-catalogue-pipeline
- BioTools-Dev/RaPDTool
- microbiome/OMA
- DiltheyLab/MetaMaps
- lisphilar/covid19-sir
- epi2me-labs/wf-metagenomics
- tristan-hyams/turbocookedrabbit
- louiejtaylor/grabseqs
- taowenmicro/EasyMultiOmics
- pirovc/ganon
- styczynski/bioseqdb
- jolespin/veba
- EMOD-Hub/EMOD
- broadinstitute/catch
- wxwx1993/PM_COVID
- khyox/recentrifuge
- Zymo-Research/figaro
- katerinakazantseva/strainy
- CSB5/OPERA-MS
- BigDataBiology/macrel
- metagentools/GraphBin
- meringlab/FlashWeave.jl
- Trhova/Multi-omics
- ibe-uw/tiara
- AlgebraicJulia/AlgebraicPetri.jl
- biocore/gemelli
- EBI-Metagenomics/mettannotator
- donovan-h-parks/STAMP
- zellerlab/GECCO
- biobakery/maaslin3
- StevenWingett/FastQ-Screen
- borenstein-lab/microbiome-metabolome-curated-data
- SPAAM-community/AncientMetagenomeDir
- patrickwest/EukRep
- Vini2/phables
- seqan/lambda
- linxingchen/cobra
- jhuapl-bio/taxtriage
- starschema/COVID-19-data
- rrwick/Metagenomics-Index-Correction
- ConnorDonegan/geostan
- rhysnewell/Lorikeet
- qiyunzhu/woltka
- Merck/Sapiens
- nf-core/hlatyping
- broadinstitute/pyro-cov
- xinehc/args_oap
- KarstensLab/microshades
- cmkobel/CompareM2
- songweizhi/MetaCHIP
- robert-koch-institut/COVID-19-Hospitalisierungen_in_Deutschland
- Kalan-Lab/zol
- RVanDamme/MUFFIN
- JamieHeather/stitchr
- Arkadiy-Garber/FeGenie
- dnbaker/bonsai
- FOI-Bioinformatics/flextaxd
- statdivlab/radEmu
- metagentools/MetaCoAG
- vrmarcelino/CCMetagen
- bhattlab/kraken2_classification
- will-rowe/groot
- mtisza1/Cenote-Taker3
- lmrodriguezr/nonpareil
- cmmr/EsViritu
- transcript/samsa2
- HUST-NingKang-Lab/MGM
- ohmeta/metapi
- iquasere/KEGGCharter
- muellan/metacache
- alesssia/YAMP
- leylabmpi/Struo2
- P-kai/EasyNanoMeta
- instadeepai/FrameDiPT
- whitews/FlowIO
- pengxingang/TEIM
- dib-lab/charcoal
- smdabdoub/kraken-biom
- microbiome/mia
- bluenote-1577/fairy
- genotoul-bioinfo/Binette
- svalkiers/clusTCR
- soedinglab/WIsH
- will-rowe/hulk
- biocore/empress
- Serka-M/mmlong2
- rhysnewell/rosella
- antigenomics/arda
- dmnfarrell/epitopepredict
- qmarcou/IGoR
- biocore/emperor
- LuoGroup2023/PanTax
- vmikk/metagMisc
- xuechunxu/DiTing
- cafferychen777/MicrobiomeStat
- flowhub-team/Metagenomics
- LaboratorioBioinformatica/MARVEL
- yuezhengfu/CNPS.cycle
- anuradhawick/kmertools
- marbl/MetagenomeScope

## Caveats

- Static validation only; real grading needs an LLM judge key + Docker.
- inline_dockerfile mode skips image build (no Docker daemon needed to publish).
- Provider secrets in upstream diffs were redacted before public release.
