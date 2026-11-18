# Issue

**Title:** Use coverage for NanoSim long-read simulations

## Description

## Summary
- calculate genome sizes and propagate them so NanoSim metagenomic simulations can request coverage instead of fixed read counts
- update both fasta and fastq NanoSim3 metagenomic processes to pass coverage derived from normalized abundances and total bases
- add genome-size tracking to the metatranscriptomic NanoSim3 workflow and use coverage when simulating transcriptome reads

## Testing
- not run (not requested)

------
[Codex Task](https://chatgpt.com/codex/tasks/task_e_69303bc46900832ab0e642f8baac34e0)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7717c790f5fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.