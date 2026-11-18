# Issue

**Title:** [MRG] better integrate protein search of unitigs into spacegraphcats

## Description

Note: PR into 

This PR updates code in #379 to make use of the new `sourmash.MinHash.seq_to_hashes(...)` functionality available in [sourmash 4.2.2](https://github.com/sourmash-bio/sourmash/releases/tag/v4.2.2) to do cleaner and (maybe?) faster protein search of unitigs.

specifically, vs #379, this PR -
* moves the script to `spacegraphcats/search/query_by_prot.py`
* replaces the custom / janky `translate(...)` code so that `MinHash.seq_to_hashes(...)` and hashvals are used instead
* adds a `--query-is-dna` to enable translated search of DNA x DNA queries (think tblastx)
* adds simple automated tests to `test_dory_workflow.py`
* removes `scripts/translate-unitigs.py` as unnecessary
* fixes a bug in protein ksize calculation when constructing MinHash objects

Note, this is still an "exact" search - the sourmash code is used to do translation, but no downsampling is done.

## minimal validation of test data

I constructed the test data like so:
* I took a subset of the dory unitigs, and BLASTed them against nr; this gave me `OQR80224.1 NHP2 protein 1-like [Tropilaelaps mercedesae]`, which I put in `data/dory-prot-query.faa`.
* I then isolated all matching contigs with `python -m spacegraphcats.search.query_by_prot data/dory-prot-query.faa dory_k21/bcalm.unitigs.db` and put the two resulting unitigs in `data/dory-dna-translate-query.fa`
* I round-trip-validated with the following:

```
makeblastdb -in data/dory-prot-query.faa -dbtype prot
blastx -query data/dory-dna-translate-query.fa -db data/dory-prot-query.faa
```
which gave me this output:
```
Query= 145

Length=212
                                                                      Score     E
Sequences producing significant alignments:                          (Bits)  Value

  OQR80224.1 NHP2 protein 1-like [Tropilaelaps mercedesae]            129     1e-45


> OQR80224.1 NHP2 protein 1-like [Tropilaelaps mercedesae]
Length=127

 Score = 129 bits (323),  Expect = 1e-45, Method: Compositional matrix adjust.
 Identities = 58/70 (83%), Positives = 65/70 (93%), Gaps = 0/70 (0%)
 Frame = +3

Query  3    LVQQAMNYKQLRKGANEATKSLNRGKAELIVMAGDSNPIEILLHLPLLCEDKNVPYVFVP  182
            LVQQA NYKQ+RKGANEATK+LNRG +E+I+M+ D+NPIEILLHLPLLCEDKNVPYVFVP
Sbjct  24   LVQQATNYKQIRKGANEATKTLNRGISEMIIMSADANPIEILLHLPLLCEDKNVPYVFVP  83

Query  183  SKAALGRAAG  212
            SK ALGRA G
Sbjct  84   SKTALGRACG  93
...
Query= 63

Length=436
                                                                      Score     E
Sequences producing significant alignments:                          (Bits)  Value

  OQR80224.1 NHP2 protein 1-like [Tropilaelaps mercedesae]            173     1e-61


> OQR80224.1 NHP2 protein 1-like [Tropilaelaps mercedesae]
Length=127

 Score = 173 bits (438),  Expect = 1e-61, Method: Compositional matrix adjust.
 Identities = 91/124 (73%), Positives = 107/124 (86%), Gaps = 0/124 (0%)
 Frame = +2

Query  14   EVNPKAFPLADTDMTRKTLELIQQACNYKQLRKGANEATKALNRGISEFVVLAADTeple  193
            EVNPKA+PLAD D++ K L L+QQA NYKQ+RKGANEATK LNRGISE ++++AD  P+E
Sbjct  4    EVNPKAYPLADPDLSTKILNLVQQATNYKQIRKGANEATKTLNRGISEMIIMSADANPIE  63

Query  194  illhlpllCEDKNVPYVFVPSKQALGRACGVSRPVISCSVTVNEGSQLKPQINTLKNEIE  373
            ILLHLPLLCEDKNVPYVFVPSK ALGRACGVSR VI+ SVT NEGSQLK Q+  L+ E+E
Sbjct  64   ILLHLPLLCEDKNVPYVFVPSKTALGRACGVSRSVIAVSVTTNEGSQLKTQVEALRGEVE  123

Query  374  RLLI  385
            +LL+
Sbjct  124  KLLV  127
```
which confirmed with blastx that that DNA query matched that protein result.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c65d04fcce4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.