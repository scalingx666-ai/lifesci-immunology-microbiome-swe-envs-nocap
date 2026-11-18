# Issue

**Title:** Fix input channels

## Description

This handles BAM files differently and creates a map out of given BAM files that matches the input from `Channel.fromFilePairs()` identically, thus not creating any error:

```
[name, /path/to/bam/file]
``` 

The `test.config` profile should run through fine, also the tests using the following commandline runs fine for me locally:

```
nextflow run . --reads "/Users/alexanderpeltzer/IDEA/nf-core/test-datasets/bam/*.bam" --dna -profile docker --bam -dump-channels
N E X T F L O W  ~  version 18.10.1
Launching `./main.nf` [angry_waddington] - revision: ab5f3df06c
=========================================
 nf-core/hlatyping v1.2dev
=========================================
Run Name       : angry_waddington
Reads          : /Users/alexanderpeltzer/IDEA/nf-core/test-datasets/bam/*.bam
Data Type      : Paired-End
File Type      : BAM
Index Location : /Users/alexanderpeltzer/IDEA/nf-core/hlatyping/data/indices/yara/hla_reference_dna
IP solver      : glpk
Enumerations   : 1
Beta           : 0.009
Prefix         : hla_run
Max Memory     : 128 GB
Max CP Us      : 16
Max Time       : 10d
Output dir     : ./results
Working dir    : /Users/alexanderpeltzer/IDEA/nf-core/hlatyping/work
Container      : nfcore/hlatyping:latest
Current home   : /Users/alexanderpeltzer
Current user   : alexanderpeltzer
Current path   : /Users/alexanderpeltzer/IDEA/nf-core/hlatyping
Script dir     : /Users/alexanderpeltzer/IDEA/nf-core/hlatyping
Config Profile : docker
=========================================
BAM file format detected. Initiate remapping to HLA alleles with yara mapper.
[warm up] executor > local
[9a/fb7557] Submitted process > output_documentation (1)
[c0/9dd891] Submitted process > make_ot_config
[2f/9fc402] Submitted process > remap_to_hla (1)
[15/60c78e] Submitted process > get_software_versions
[17/ca8ec5] Submitted process > multiqc
[53/532690] Submitted process > run_optitype (1)
WARN: To render the execution DAG in the required format it is required to install Graphviz -- See http://www.graphviz.org for more info.
```


Other fixes:

- get rid of the email template (no need apparently anymore)
- update `$params.version` to `$workflow.manifest.version` everywhere
- add a default for `readPaths` to get rid of the warning when not specifying `readPaths`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db505dd59320`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.