# Issue

**Title:** Update to use struct acsets

## Description

Updated to be compatible with catlab struct acsets. A couple things to note:

1. I had to change the signatures of `Open(p::AbstractReactionNet{R,C})` and `Open(p::AbstractLabelledReactionNet{R,C})` to just `Open(p::ReactionNet{R,C})` and `Open(p::LabelledReactionNet{R,C})` because I don't think the new abstract acset types have any notion of being parameterized by types (they are not created from a schema). The disadvantage of this is you can no longer pass custom subtypes of rxn nets to `Open`. I'm assuming there's a way to re-generalize this code under the new system but I haven't figured it out yet so any input would be appreciated.
2. Sort of in the same vein as 1, I changed `function petri_homomorphisms(p1::T, p2::T; kw...) where {CD, AD, T <: AbstractACSet{CD,AD}}` to just `function petri_homomorphisms(p1::AbstractPetriNet, p2::AbstractPetriNet; kw...)` for the same reason as above. This works but we lose the compile-time checking that p1 and p2 are instances of the same schema. Again, I'm assuming there's probably a way to add this back in if we want.

Also, this is my first ever pr to anything larger than a small group project so go easy on me 😄

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91535bd5aea8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.