# Issue

**Title:** Feature/refactor lca header coding style

## Description

There are **no functional changes** whatsoever in this PR, it's purely cosmetic. This is part 1 of a two-part small effort to refactor `LCA.hpp`. Small points regarding this PR:

- remove `using namespace std`: it is not encouraged to do `using namespace` of any kind in a header file, as it bleeds the namespace scope into the scope of whoever includes the header;

- move `private` members to the bottom of the class definition: this is just a bit more C++ idiomatic, but the idea is that clients of a class should yield the public part and be totally unaware of the private implementation. Let's then present the public part first, at the top of the class;

- the calls to `<cmath>` are qualified with `std::`: if we include `<cmath>` (and not `<math.h>`), let's call the interface provided by C++ and not pure C;

- use prefix `m_` for member variables: this is a coding standard we already see in other classes of `ganon`. The good thing about this is that it becomes pretty clear what is private and we avoid name clashes (we had calls like `this->depth` and parameters names `_depth`).

Stern me up! :beer:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d40b436878c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.