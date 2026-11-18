# Issue

**Title:** Update three.js and bug fixes

## Description

Update all the THREE.js dependencies to the latest release. The old
version had a bug where once you changed the background color
to something that's not black, you would never be able to change it
back to black (very strange).

In addition, as I worked on the problem above, I noticed that the code was mixing color representations, as hexadecimal numbers and as strings. Which lead to the AxesViewController to stop working when colors were saved as numbers and then tried to be loaded as strings. This patch changes all properties to always deal with CSS-like strings.

Finally, in the latest version of three.js the renderer's clearColor property was deprecated and replaced by the scene's background property.

**Suggestions on how to review**: Only pay attention to the changes in, all the other files are updates from THREE.js:

```
 LICENSE.md                                                         |    2 +-
 emperor/support_files/js/axes-controller.js                        |   33 +-
 emperor/support_files/js/controller.js                             |   18 +-
 emperor/support_files/js/sceneplotview3d.js                        |   22 +-
 emperor/support_files/js/view.js                                   |    8 +-
 tests/javascript_tests/test_axes_controller.js                     |   16 +-
 tests/javascript_tests/test_decomposition_view.js                  |    4 +-
 tests/javascript_tests/test_sceneplotview3d.js                     |    8 +-
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce83f68d80c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.