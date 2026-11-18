# Issue

**Title:** Generate command line for report without external call to ps

## Description

An improvement of the suggestion in #116 
I originally discovered this issue when trying to run KrakenUniq in Singularity with the Biocontainer built from the conda releases (in this case the container with tag `1.0.0--pl5321h19e8d03_0`) where the version of `ps` used apparently doesn't support the same command line arguments as were used in the original report generation code to produce a string with the command line used to call krakenuniq. 

Here are examples of the command lines of the report:
## Original code
```
# CL:perl /ceph/home/boulund/work/stag-uniq/.snakemake/conda/207ba047bd7ea05bc7d1265affc0c46c/bin/krakenuniq --db /ceph/db/krakenuniq/minikraken_20171013_4GB --threads 4 --output output_dir/krakenuniq/test1.kraken.gz --report-file output_dir/krakenuniq/test1.kreport --paired output_dir/host_removal/test1_1.fq.gz output_dir/host_removal/test1_2.fq.gz

```

## This PR
```
# CL:/ceph/home/boulund/work/stag-uniq/.snakemake/conda/207ba047bd7ea05bc7d1265affc0c46c/bin/krakenuniq --db /ceph/db/krakenuniq/minikraken_20171013_4GB --threads 4 --output output_dir/krakenuniq/test1.kraken.gz --report-file output_dir/krakenuniq/test1.kreport --preload-size 2G --paired output_dir/host_removal/test1_1.fq.gz output_dir/host_removal/test1_2.fq.gz
```

I know the initial `perl` isn't included, but it's easy to add if you find it important to keep.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bb224c15c00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.