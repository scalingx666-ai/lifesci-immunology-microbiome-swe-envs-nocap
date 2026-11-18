# Issue

**Title:** Fix SMG exclusion in get_components: check whole component b4 scoring PHROGs

## Description

component_utils.get_components had two related gaps in how it kept bacterial single-copy marker genes (SMGs) out of candidate phage components, despite the docstring saying "components with PHROGs and no SMGs":

1. Multi-unitig components: the loop checked each unitig for an SMG and broke on the first one found, but a `break` only stops the loop -- it doesn't clear PHROG-category flags a unitig earlier in the same component already set. So whether a mixed bacterial/phage component got excluded depended on which unitig igraph happened to iterate first, not on whether an SMG was actually present. A component with a PHROG-bearing unitig visited before an SMG-bearing one survived with the marker gene intact; the same two unitigs in the opposite order got correctly excluded.

2. Single-unitig components had no SMG check at all -- a lone unitig carrying both a marker gene and a PHROG hit was always kept.

Fixed by checking every unitig in a component for an SMG membership up front, in its own pass, before any PHROG scoring happens for either the multi- or single-unitig case. A component with any SMG is skipped outright; there's no point scoring PHROG evidence for one that's excluded either way.

Verified with a standalone test (four cases: PHROG-then-SMG order, SMG-then- PHROG order, a single unitig with both, and a clean SMG-free control) -- before the fix, the first case was incorrectly kept; after, all mixed cases are excluded and the clean case is unaffected. Also ran the real pipeline against phables' own bundled test_data/ fixture: component count is unchanged there (6), as expected -- that fixture has no marker-gene hits at all, so it doesn't exercise this path either way, but confirms nothing else regressed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4277a842e3e5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.