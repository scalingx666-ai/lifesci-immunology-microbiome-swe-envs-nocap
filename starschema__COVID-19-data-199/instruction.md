# Issue

**Title:** Jhu fips fix

## Description

fixed issue #197 where:

- 283 FIPS codes don't have leading zeros to 5 characters in the JHU_COVID_19 table

partially fixed:
- three FIPS codes (66, 72, 78) have codes but no names which should be impossible.

66, 72, 78 are referring to 66000=GU=GUAM, 72000=PR=PUERTO RICO, 78000=VI=VIRGIN ISLANDS OF THE UNITED STATES which are County-Equivalent Entities. Some rows of JHU_COVID_19 contain these entities with- and without trailing zeros, some rows have leading zeros (incorrect). For data consistency, this fix resolves 66, 72, 78 by formatting the fips with trailing zeros. These entities have NULL value as COUNTY.

unsolved:
- Some counties exist with the value "unassigned". These are usually paired with FIPS code being NULL.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83aa4ec7cbc1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.