# Issue

**Title:** Feature/refactor lca

## Description

Part-two of refactoring `LCA`. The goal here was:

1. avoid string copies (const references);
2. avoid accessing containers twice for the same values (ok, the compiler might optimize this away, but just to be on the safe side);
3. add some asserts;
4. remove smart pointers for arrays (vector was preferred).

@pirovc, as we discussed, I am handing this over to you now as there are some issues on `LCA` that you need to fix. I left a few **TODO** comments as suggestions for you. Please, make `LCA::getLCA( const std::vector< std::string >& )` a const member function =)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `260dea8af0af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.