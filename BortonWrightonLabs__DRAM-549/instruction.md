# Issue

**Title:** ci: require conventional PR titles; fix git-cliff commit bodies

## Description

## Summary

Feature PRs into `dev` are now squash-only (ruleset), so the squashed commit's title comes from the PR title (or the single commit's title), and git-cliff groups the changelog by it.

```diff
 .github/workflows/
   ci.yaml
+  pr-title.yml     # fails a PR whose title (or single commit) isn't feat:/fix:/docs:/...
 cliff.toml
+  groups: Build, Revert (every type the check allows); Package kept for history
-  body: commit.body + footers joined with ", "
+  body: raw message after the title
+  preprocessors: drop Co-authored-by; "(#123)" -> PR link
```

The body bug: git-cliff reads any paragraph starting `Word:` as a git trailer, so bodies were cut at `Tests:`, `Files:`, `BREAKING CHANGE:` or `fix:`, and the rest was glued back on one line.

## Evidence

- **Before** (`git cliff`, the test-suite commit):
  ```
      tRNAs counted 25)., Tests:- PR gate: pytest for combine_annotations, hmm_parser, rename_headers,
    generate_gff, ...
  - CI checks out the dram-rules submodule ...
  ```
  **After:**
  ```
      tRNAs counted 25).

    Tests:
    - PR gate: pytest for combine_annotations, hmm_parser, rename_headers,
      generate_gff, ...
    - CI checks out the dram-rules submodule ...
  ```
- Regenerating the whole changelog changes 110 lines, all of them entries that were run together (`, fix:…`, `, BREAKING CHANGE:…`, `, Files:…`); nothing else moves.
- `git cliff --with-commit` checks: a `Co-authored-by:` trailer is dropped; `feat: try (#12)` renders `Try ()`.
- This PR's own title is checked by the new workflow.

## Merge Danger

**Door:** two-way

**Blast Radius:** PRs

Once `conventional-title` is required on `dev`, open PRs into `dev` need a conventional title and must contain this workflow (rebase on `dev`) before they can merge. `CHANGELOG.md` isn't regenerated here; the fixed formatting shows up the next time it is.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a014160cce9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.