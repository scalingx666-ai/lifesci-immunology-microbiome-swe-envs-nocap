# Issue

**Title:** Fix/amrfinder report contigs

## Description

AMRfinderplus report improvement. New fields were added to the table and the type of the MGE is now specified when location = mobilome. An output example:

```bash
gene_id	contig_id	gene_start	gene_end	ref_coverage	ref_identity	class_summary	ref_gene_name	ref_sequence_name	location
GNBBHOPO_00175	ERZ13633678.1-NODE-1-length-230215-cov-8.265911	182476	183627	100.00	100.00	AMR|AMR|EFFLUX|EFFLUX	mexA	multidrug efflux RND transporter periplasmic adaptor subunit MexA	chromosome
NA	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	3	275	63.19	100.00	STRESS|METAL|MERCURY|MERCURY	merR	mercury resistance transcriptional regulator MerR	mobilome:plasmid
GNBBHOPO_02489	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	347	697	100.00	100.00	STRESS|METAL|MERCURY|MERCURY	merT	mercuric transport protein MerT	mobilome:plasmid
GNBBHOPO_02490	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	711	986	100.00	100.00	STRESS|METAL|MERCURY|MERCURY	merP	mercury resistance system periplasmic binding protein MerP	mobilome:plasmid
GNBBHOPO_02491	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	1174	2883	100.00	98.95	STRESS|METAL|MERCURY|MERCURY	merA	mercury(II) reductase	mobilome:plasmid
GNBBHOPO_02492	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	2919	3572	100.00	100.00	STRESS|METAL|MERCURY|PHENYLMERCURY	merG	phenylmercury resistance protein MerG	mobilome:plasmid
GNBBHOPO_02493	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	3653	4291	100.00	99.53	STRESS|METAL|MERCURY|ORGANOMERCURY	merB	organomercurial lyase MerB	mobilome:plasmid
GNBBHOPO_02495	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	5269	5703	100.00	100.00	STRESS|METAL|MERCURY|MERCURY	merR	mercury resistance transcriptional regulator MerR	mobilome:plasmid
GNBBHOPO_02497	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	6001	6639	100.00	100.00	STRESS|METAL|MERCURY|ORGANOMERCURY	merB	organomercurial lyase MerB	mobilome:plasmid
GNBBHOPO_02498	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	6751	7116	100.00	100.00	STRESS|METAL|MERCURY|MERCURY	merD	mercury resistance co-regulator MerD	mobilome:plasmid
GNBBHOPO_02499	ERZ13633678.18-NODE-18-length-106543-cov-7.185880	7113	7349	98.72	85.71	STRESS|METAL|MERCURY|MERCURY	merE	broad-spectrum mercury transporter MerE	mobilome:plasmid
GNBBHOPO_04276	ERZ13633678.41-NODE-41-length-61116-cov-8.431912	41031	41819	100.00	100.00	AMR|AMR|BETA-LACTAM|BETA-LACTAM	blaOXA-488	OXA-50 family oxacillin-hydrolyzing class D beta-lactamase OXA-488	chromosome
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c83fb88b386c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.