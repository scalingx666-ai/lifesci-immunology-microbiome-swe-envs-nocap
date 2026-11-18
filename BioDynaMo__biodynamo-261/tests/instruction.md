# Issue

**Title:** Add new paraview build

## Description

Modified ParaView for macOS on eos storage to react to `cmake` update 3.22.3 to 3.23.0. Error message:

```
CMake Error at build/third_party/paraview/lib/cmake/paraview-5.10/vtk/VTK-targets.cmake:717 (set_target_properties):
  The link interface of target "VTK::RenderingRayTracing" contains:

    ospray::ospray

  but the target was not found.  Possible reasons include:

    * There is a typo in the target name.
    * A find_package call is missing for an IMPORTED target.
    * An ALIAS target is missing.

Call Stack (most recent call first):
  build/third_party/paraview/lib/cmake/paraview-5.10/vtk/vtk-config.cmake:138 (include)
  build/third_party/paraview/lib/cmake/paraview-5.10/paraview-config.cmake:66 (find_package)
  CMakeLists.txt:376 (find_package)

```

Fixed by removing `;ospray::ospray` from `VTK-targets.cmake`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9b05ef22b03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.