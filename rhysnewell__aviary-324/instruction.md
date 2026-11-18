# Issue

**Title:** Fix metabuli trailing tab

## Description

## Fixes to the Metabuli extra tab trail within the tax_classifications.tsv 

- Metabuli has two different row endings depending on is_classified. Classified rows (is_classified = 1) end with "\n". Unclassified rows (is_classified = 0) end with "-\t\n", an extra trailing tab. This gives unclassified rows 9 tab-separated fields against classified rows 8. When Aviary reads the file via pandas, this inconsistency causes: 
`pandas.errors.ParserError: Error tokenizing data. C error: Expected 8 fields in line X, saw 9`

---
### The fix:
- Pin pandas to read only the first 8 columns (usecols=range(8)). This fixes the trailing field on unclassified rows without discarding real data. Also, if Metabuli's own code is later fixed, this same code won't error, since 8 columns is still what gets read either way.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `82885793506a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.