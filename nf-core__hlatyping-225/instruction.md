# Issue

**Title:** fix: typo in HLAHD_INSTALL; added hlahd_update_reference_dict to catch errors in dictionary update

## Description

Hi Jonas,

I got the following error when trying to run `HLAHD_INSTALL` with `--hlahd_update_reference_dict`:

```sh
sh: 0: cannot open update_dictionary.sh: No such file
```

I checked the work folder and manually examined the HLA-HD tarball and found that the script name was actually `update.dictionary.sh` (I also confirmed my tarball hash matches yours in the script):

```bash
$ cd hlahd.1.7.1 && ls -1
/home/vajith/my_scratch/hlahd.1.7.1
bin
data
dictionary
estimation
freq_data
HLA_gene.split.3.32.0.txt
HLA_gene.split.3.50.0.txt
HLA_gene.split.txt
install.sh
Readme.txt
src
update.dictionary.sh
```

When I fixed the typo in the work folder the process found the path correctly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c0fb9b96091`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.