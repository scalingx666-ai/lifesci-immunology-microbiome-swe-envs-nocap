# Issue

**Title:** add informative error throw if node file (point_file) contains non-integers

## Description

Related and in response to #257, . Throw an error if the point_file contains non-integer values. Circuitscape originally converted point_file to Int64 (or Int32, based on the `T` argument) inside `read_raster`. 

I pulled the conversion of the node array out of `_grid_reader` and `read_raster` to avoid making changes to `read_raster` that would have downstream implications for Omniscape, and to make this error only possible when reading the point_file via `read_polymap`.

With this fix, if you have a point_file with non integers, you will get output like this:
```julia
┌ Error: Your node file (point_file in the .ini) contains non-integer values. See the docs on specifying nodes for more information.
└ @ Circuitscape /home/omniscape/src/io.jl:147
ERROR: InexactError: Int64(0.0010000000474974513)
Stacktrace:
 [1] Int64 at ./float.jl:710 [inlined]
 [2] _broadcast_getindex_evalf at ./broadcast.jl:648 [inlined]
 [3] _broadcast_getindex at ./broadcast.jl:621 [inlined]
 [4] getindex at ./broadcast.jl:575 [inlined]
 [5] macro expansion at ./broadcast.jl:932 [inlined]
 [6] macro expansion at ./simdloop.jl:77 [inlined]
 [7] copyto! at ./broadcast.jl:931 [inlined]
 [8] copyto! at ./broadcast.jl:886 [inlined]
 [9] copy(::Base.Broadcast.Broadcasted{Base.Broadcast.DefaultArrayStyle{1},Tuple{Base.OneTo{Int64}},Type{Int64},Tuple{Array{Float64,1}}}) at ./broadcast.jl:862
 [10] materialize at ./broadcast.jl:837 [inlined]
 [11] read_point_map(::Type{T} where T, ::String, ::Circuitscape.RasterMeta) at /home/Circuitscape/src/io.jl:225
 [12] load_raster_data(::Type{T} where T, ::Type{T} where T, ::Dict{String,String}) at /home/Circuitscape/src/io.jl:415
 [13] raster_pairwise(::Type{T} where T, ::Type{T} where T, ::Dict{String,String}) at /home/Circuitscape/src/raster/pairwise.jl:18
 [14] _compute(::Type{T} where T, ::Type{T} where T, ::Dict{String,String}) at /home/Circuitscape/src/run.jl:42
 [15] macro expansion at ./timing.jl:233 [inlined]
 [16] compute(::String) at /home/Circuitscape/src/run.jl:31
 [17] top-level scope at untitled-63407bae533d0dff06914a870a28bed2:2
 [18] include_string(::Function, ::Module, ::String, ::String) at ./loading.jl:1088
```
cc @ViralBShah

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe44391055d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.