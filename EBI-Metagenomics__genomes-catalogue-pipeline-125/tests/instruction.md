# Issue

**Title:** Fix/trna detect nfs tmp

## Description

Fixing issue:
```
 ------------------------------------------------------------
 Sequence file(s) to search:    MGYG000519425.fna
 Search Mode:            Bacterial
 Results written to:        MGYG000519425_trna.out
 Output format:           Tabular
 Searching with:          Infernal First Pass->Infernal
 Isotype-specific model scan:    Yes
 Covariance model:         /opt/conda/lib/tRNAscan-SE/models/TRNAinf-bact.cm
                   /opt/conda/lib/tRNAscan-SE/models/TRNAinf-bact-SeC.cm
 Infernal first pass cutoff score: 10
  
 Temporary directory:        /hps/nobackup/rdf/metagenomics/service-team/nextflow-workdir/users/kates/tmp.8sFIpgYEKe
 tRNA predictions saved to:     MGYG000519425_trna.gff
 Search statistics saved in:    MGYG000519425_stats.out
 ------------------------------------------------------------
  
 rm: cannot remove '/hps/nobackup/rdf/metagenomics/service-team/nextflow-workdir/users/kates/tmp.8sFIpgYEKe/.nfs0b88441b8983854300057e22': No such file or directory
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f9aeeb897fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.