# Issue

**Title:** Fix tool execution if annotation workflow is skipped

## Description

I noticed that in the case that only tools are activated which don't require annotation (so that annotation workflow is skipped), those tools are not executed at all.

This PR fixes the missing input for prediction tools (whose execution is then not triggered) if annotation workflow is skipped.
- `ampcombi/parsetables` requires annotation files in any case, hence I removed any tool filtering in the if statement.
- the contig fasta (`ch_intermediate_input.fastas`) is required as input for tools that don't need annotation (fargene, amrfinderplus, rgi, abricate, macrel)

Without this update: tool executed not triggered
![image](https://github.com/user-attachments/assets/5b54364b-69fa-4b46-ba80-7ce98dc34a52)

With this update: tool executed triggered
![image](https://github.com/user-attachments/assets/2771d991-0851-42f0-8bf7-655505a13051)

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d482e7ddc4f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.