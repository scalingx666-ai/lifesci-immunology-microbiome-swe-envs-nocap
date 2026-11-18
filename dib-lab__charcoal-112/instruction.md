# Issue

**Title:** enable lineages csv that does not contain trailing commas

## Description

If the lineages csv does not have a trailing comma:
`GCF_000317415.1.fna.gz,d__Eukaryota` vs `GCF_000317415.1.fna.gz,d__Eukaryota,`
 it is not interpreted as a proper lineages file.


error:
```
charcoal run orthodb/orthodb.conf -n
** cannot parse provided lineage for GCF_000317415.1.fna.gz
** ; is it comma separated?
SystemExit in line 98 of /home/ntpierce/charcoal/charcoal/Snakefile:
-1
  File "/home/ntpierce/charcoal/charcoal/Snakefile", line 98, in <module>
Error in snakemake invocation: Command '['snakemake', '-s', '/home/ntpierce/charcoal/charcoal/Snakefile', '--use-conda', '-j', '1', '-n', '--configfile', '/home/ntpierce/charcoal/charcoal/conf/defaults.conf', '/home/ntpierce/charcoal/charcoal/conf/system.conf', 'orthodb/orthodb.conf']' returned non-zero exit status 1.
```

switching line 95 `if len(row[1:]) <= 1:` to `if len(row[1:]) < 1:` fixes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b92aec1b3e30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.