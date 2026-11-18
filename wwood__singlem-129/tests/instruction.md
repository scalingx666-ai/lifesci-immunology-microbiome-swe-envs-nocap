# Issue

**Title:** Enable processing of tree-less GraftM packages

## Description

Fixes a bug where package_creator attempts to load the GraftM package tree when it doesn't exist. 

For example:
```
bin/singlem create --target_domains Viruses --gene-description '' --input-graftm-package /home/n10927662/rossenzhao/vogdb211/metapackage-v5-making/redo/gpkgs/VOG00589.gpkg --hmm-position 88 --input-taxonomy /home/n10927662/rossenzhao/vogdb211/metapackage-v5-making/refseq-imgvr-taxonomy.tsv --output-singlem-package /home/n10927662/rossenzhao/vogdb211/metapackage-v5-making/redo/spkgs/VOG00589.spkg

05/10/2023 03:52:00 PM INFO: SingleM v1.0.0beta5
05/10/2023 03:52:02 PM INFO: Detected package type as protein
Traceback (most recent call last):
  File "/home/n10927662/singlem/bin/singlem", line 856, in <module>
    PackageCreator().create(input_graftm_package = args.input_graftm_package,
  File "/mnt/hpccs01/home/n10927662/singlem/bin/../singlem/package_creator.py", line 38, in create
    path=gpkg.reference_package_tree_path(),
  File "/home/n10927662/e/singlem/lib/python3.10/site-packages/graftm/graftm_package.py", line 160, in reference_package_tree_path
    self._refpkg_contents()['files']['tree'])
KeyError: 'tree'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3be32181a0a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.