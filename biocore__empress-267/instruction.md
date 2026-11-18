# Issue

**Title:** Apply linting and stylechecking to JS test files

## Description

This PR doesn't add any functionality to Empress. All it does is include the test JS files in `make stylecheck` and `make jsstyle`. This'll be nice going forward, because it'll help keep these tests linted and looking consistent with the rest of the JS codebase.

(Figured it'd be easiest to add this in as its own PR, so that these changes can be reviewed in isolation.)

Most of the changes here are pretty minor stylistic things (e.g. single -> double quotes, spacing), but there are a handful of more substantial things that should probably be looked over. Some of these things I can think of:

1. The tree data in `test-empress.js` had duplicate `inSample` keys (each node had both a `false` and `true` version of this key set when initialized). I think that only the `true`s were being kept (also, if you remove all the `false`s nothing changes, but if you remove all the `true`s instead then one of the tests breaks), but another set of eyes on this code might be nice.

2. There are a few places in the tests where a negative value was used as the right term in a subtraction, e.g. [this line](https://github.com/biocore/empress/compare/master...fedarko:style-js-tests?expand=1#diff-79e9258925e6e54eb935a04856f3c4bbR33) which used `angle.sin - (-1/2)`. I ran prettier first, which (IIRC) changed this to `angle.sin - -1 / 2`, and then jshint complained about that, so I wound up just changing this to `angle.sin + 1 / 2`. But I can see how the first version of this might be preferable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da3307e69c7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.