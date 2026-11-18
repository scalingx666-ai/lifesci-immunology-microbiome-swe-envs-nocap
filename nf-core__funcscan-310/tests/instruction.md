# Issue

**Title:** fix input schema to accept uncompressed fasta; fix #309

## Description

<!--
# nf-core/funcscan pull request

Many thanks for contributing to nf-core/funcscan!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

----

This should fix #309 that errors when uncompressed files are given as input. 
I also added support for `fas` extension. 

I have tested the workflow using all uncompressed and compressed formats as input.

<details><summary>Click here for code used to generate the test data.</summary>

```bash
mkdir -p data

# download test data
# wget didn't actually work, downloaded it manually
wget -O data/s1.fasta.gz "https://raw.githubusercontent.com/nf-core/test-datasets/funcscan/wastewater_metagenome_contigs_1.fasta.gz"
wget -O data/s2.fasta.gz "https://raw.githubusercontent.com/nf-core/test-datasets/funcscan/wastewater_metagenome_contigs_2.fasta.gz"

# make uncompressed copies with different extensions
# and populate a samplesheet
echo "sample,fasta" > samplesheet.csv
for i in s1 s2
do
  # add the original fasta to samplesheet
  echo "${i}_fasta,data/$i.fasta" >> samplesheet.csv
  echo "${i}_fasta.gz,data/$i.fasta.gz" >> samplesheet.csv

  # uncompressed version
  gzcat data/$i.fasta.gz > data/$i.fasta

  # copies of each extension
  for j in fas fa fna
  do
    cp data/$i.fasta.gz data/$i.$j.gz
    cp data/$i.fasta data/$i.$j

    # populate the samplesheet
    echo "$i,data/$i.$j" >> samplesheet.csv
    echo "$i,data/$i.$j.gz" >> samplesheet.csv
  done
done
```

</details>

The code above generates the files and respective samplesheet: 

```
sample,fasta
s1_fasta,data/s1.fasta
s1_fasta_gz,data/s1.fasta.gz
s1_fas,data/s1.fas
s1_fas_gz,data/s1.fas.gz
s1_fa,data/s1.fa
s1_fa_gz,data/s1.fa.gz
s1_fna,data/s1.fna
s1_fna_gz,data/s1.fna.gz
s2_fasta,data/s2.fasta
s2_fasta_gz,data/s2.fasta.gz
s2_fas,data/s2.fas
s2_fas_gz,data/s2.fas.gz
s2_fa,data/s2.fa
s2_fa_gz,data/s2.fa.gz
s2_fna,data/s2.fna
s2_fna_gz,data/s2.fna.gz
```

I then ran the test as follows (`funcscan/main.nf` points to my local clone): 

```bash
nextflow funcscan/main.nf -profile test,singularity --input samplesheet.csv --outdir results
```

This mixed bag of formats all worked successfully:

```
executor >  local (398)
[a6/b62a61] process > NFCORE_FUNCSCAN:FUNCSCAN:GUNZIP_FASTA_PREP (s1.fas.gz)                      [100%] 8 of 8 ✔
[f5/6d0393] process > NFCORE_FUNCSCAN:FUNCSCAN:BIOAWK (s1_fas_gz)                                 [100%] 16 of 16 ✔
[c0/b6267f] process > NFCORE_FUNCSCAN:FUNCSCAN:PRODIGAL_GFF (s1_fas_gz)                           [100%] 16 of 16 ✔
[e3/ef2c17] process > NFCORE_FUNCSCAN:FUNCSCAN:GUNZIP_PRODIGAL_FAA (s1_fas_gz.faa.gz)             [100%] 16 of 16 ✔
[dc/d89187] process > NFCORE_FUNCSCAN:FUNCSCAN:GUNZIP_PRODIGAL_FNA (s1_fas_gz.fna.gz)             [100%] 16 of 16 ✔
[0b/f4f7bb] process > NFCORE_FUNCSCAN:FUNCSCAN:GUNZIP_PRODIGAL_GFF (s1_fas_gz.gff.gz)             [100%] 16 of 16 ✔
[25/d14230] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:AMPLIFY_PREDICT (s1_fas_gz)                    [100%] 16 of 16 ✔
[9d/ec2e9e] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:MACREL_CONTIGS (s1_fas_gz)                     [100%] 16 of 16 ✔
[a0/2d3305] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:GUNZIP_MACREL_PRED (s1_fas_gz.prediction.gz)   [100%] 16 of 16 ✔
[0c/849cee] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:GUNZIP_MACREL_ORFS (s1_fas_gz.all_orfs.faa.gz) [100%] 16 of 16 ✔
[65/1c840a] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:AMPIR (s1_fas_gz)                              [100%] 16 of 16 ✔
[ea/cc2c44] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:AMP_HMMER_HMMSEARCH (s1_fas_gz)                [100%] 16 of 16 ✔
[63/441d8b] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:DRAMP_DOWNLOAD                                 [100%] 1 of 1 ✔
[5c/a49d25] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:AMPCOMBI (s2_fa)                               [100%] 16 of 16 ✔
[55/88d7ab] process > NFCORE_FUNCSCAN:FUNCSCAN:AMP:TABIX_BGZIP (ampcombi_complete_summary)        [100%] 1 of 1 ✔
[9c/a2b5b4] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:AMRFINDERPLUS_UPDATE (update)                  [100%] 1 of 1 ✔
[19/91212b] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:AMRFINDERPLUS_RUN (s2_fa_gz)                   [100%] 16 of 16 ✔
[83/930e8d] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:HAMRONIZATION_AMRFINDERPLUS (s2_fa_gz)         [100%] 16 of 16 ✔
[88/bea5f5] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:FARGENE (s1_fas_gz)                            [100%] 32 of 32 ✔
[7a/a5fbb7] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:HAMRONIZATION_FARGENE (s1_fas_gz)              [100%] 64 of 64 ✔
[19/96f68b] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:RGI_MAIN (s1_fas_gz)                           [100%] 16 of 16 ✔
[b1/a05766] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:HAMRONIZATION_RGI (s1_fas_gz)                  [100%] 16 of 16 ✔
[86/552db3] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:ABRICATE_RUN (s1_fas_gz)                       [100%] 16 of 16 ✔
[f4/a887b2] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:HAMRONIZATION_ABRICATE (s1_fas_gz)             [100%] 16 of 16 ✔
[ff/28d892] process > NFCORE_FUNCSCAN:FUNCSCAN:ARG:HAMRONIZATION_SUMMARIZE                        [100%] 1 of 1 ✔
[f2/436bc1] process > NFCORE_FUNCSCAN:FUNCSCAN:CUSTOM_DUMPSOFTWAREVERSIONS (1)                    [100%] 1 of 1 ✔
[71/dd9844] process > NFCORE_FUNCSCAN:FUNCSCAN:MULTIQC                                            [100%] 1 of 1 ✔
-[nf-core/funcscan] Pipeline completed successfully-
Completed at: 15-Sep-2023 18:16:43
Duration    : 1h 6m 47s
CPU hours   : 2.9
Succeeded   : 398
```

Version: 

```
N E X T F L O W
version 23.04.1 build 5866
created 15-04-2023 06:51 UTC (07:51 BST)
cite doi:10.1038/nbt.3820
http://nextflow.io
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `522ca9d66b6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.