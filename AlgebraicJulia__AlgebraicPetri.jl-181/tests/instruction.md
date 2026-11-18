# Issue

**Title:** Updates for Catlab 0.17

## Description

Addresses various breaking changes in the Catlab 0.17 release. These include:

- No more `LooseACSetTransformation`: instead stratification limits are in a `LooseACSet` category of ACSets.
- Some uses of `==` in the tests replaced with `≃`
- Components of ACSetTransformations no longer assumed to be `FinFunctionVector`: to get a vector out of a `FinFunction` we now call `collect(f)` instead of `f.func`.
- `FinDomFunction` ob/hom mappings use presentation generators, not symbols.

There was one logic error in the previous implementation that was revealed in the update process: when we call `flatten_labels` to take a stratified model (which has, for example, `Name` attributes valued in *pairs* of symbols) and convert it to a regular Petri net (`Name` valued in just symbols with a `_` in the middle of the pair), the code previously did not change the components of typing hom that is going out of the model into a typing petri net. This needed to be fixed because otherwise a type error would be encountered (trying to use a function with domain `Tuple{String,String}`  when a function with domain `String` was needed).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e76f7cb476ea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.