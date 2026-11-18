# Issue

**Title:** Fix contig names in combined report and add mobile_element_type to full GFF

## Description

This PR bundles three related fixes to the mobilome annotation outputs:

  1. mobile_element_type attribute on the full GFF
  Passenger CDS in *_mobilome_full.gff now carry a mobile_element_type=<types> attribute, matching what clean/extra already provide. Also renames the attribute key mge_location → mobile_element_type across clean/extra/full for consistency.

  2. Original contig names in the combined report
  pathofact2_report.py gained an optional --contig_map argument. For the Prodigal baseline, protein contig ids are now translated back  to their original names, so combined_report.tsv's contig_id column shows the original contig (not the renamed internal id). The contigs name map file is passed only for the Prodigal baseline; user-provided proteins already carry original names, so that path is untouched.

  3. Stabilize flaky test assertions
  pathofact2.gff and combined_report.tsv are assembled from multithreaded, tie-sensitive tools (DIAMOND, hmmsearch, CD-search), making their md5 non-reproducible across CPU allocations. They're now excluded from the content-md5 snapshot (via .nftignore) and instead asserted for existence + key stable content lines (correct header, original contig name present, no renamed-id leak).

  🤖 PR description generated with Claude Code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dd30d78b8f4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.