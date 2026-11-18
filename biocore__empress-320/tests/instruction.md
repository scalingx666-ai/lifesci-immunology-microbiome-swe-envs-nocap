# Issue

**Title:** Hide feature metadata barplot controls if no feature metadata is available; add first barplot panel tests; abstract Empress initialization code for JS testing

## Description

This . If no feature metadata is used when generating a QZV, barplot layers now just show the sample metadata barplot controls:

![image](https://user-images.githubusercontent.com/4177727/89845056-4de62e80-db32-11ea-9e9f-44eccbdec3c6.png)

To make sure this isn't a problem again, this PR also adds the first tests for the `barplot-panel-handler` code\* (although the tests interact with the barplot layer code as well, so I guess we could also just call the module `test-barplots` or something...). Part of this required re-creating an Empress object, so to make life easier for us in the future I abstracted that code from the `setup` block of `test-empress.js` to a new module (`utilities-for-testing.js`, named that way in order to avoid confusion with `util.js` and `test-util.js` ._.).

I don't think it's required to merge this PR in, but **there is an issue with the barplot panel tests I haven't been able to figure out yet** -- basically, when calling `Empress.updateLayout()` during tests, I get a weird error from the `gl-matrix` code:

```
TypeError: Cannot set property '0' of undefined
    at Object.u (file:///home/marcus/Dropbox/Work/KnightLab/Empress/fedarko/empress/empress/support_files/vendor/gl-matrix.min.js:28:30362)
    at Drawer.centerCameraOn (file:///home/marcus/Dropbox/Work/KnightLab/Empress/fedarko/empress/empress/support_files/js/drawer.js:466:17)
    at Empress.centerLayoutAvgPoint (file:///home/marcus/Dropbox/Work/KnightLab/Empress/fedarko/empress/empress/support_files/js/empress.js:1896:22)
    at Empress.updateLayout (file:///home/marcus/Dropbox/Work/KnightLab/Empress/fedarko/empress/empress/support_files/js/empress.js:1783:22)
    at Object.<anonymous> (file:///home/marcus/Dropbox/Work/KnightLab/Empress/fedarko/empress/tests/test-barplot-panel-handler.js:80:17)
```

I can trace the error back to [this line](https://github.com/biocore/empress/blob/e3ed544cbab8cff7e5ea924848b3a67bfa569ce8/empress/support_files/js/drawer.js#L466) of code, but I'm not familiar enough with this to say what the problem is. Since centering the camera works perfectly fine when running Empress :), I assume that this is a problem with mocking the canvas / drawer / camera / etc. during testing that is breaking WebGL somehow. The test this error impacts isn't very critical, so I've just commented it out for now. If we can get it working, though, that'd be nice.

\* (There were already tests for many of the functions used by the barplot code, but no direct tests yet for things like the barplot HTML. This PR should make it easier to add more of those.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3ed544cbab8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.