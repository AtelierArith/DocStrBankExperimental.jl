```
mapCube(fun, cube, addargs...;kwargs...)
```

Map a given function `fun` over slices of the data cube `cube`.      The additional arguments `addargs` will be forwarded to the inner function `fun`.     Use InDims to discribe the input dimensions and OutDims to describe the output dimensions of the function.

### Keyword arguments

  * `max_cache=YAXDefaults.max_cache` Float64 maximum size of blocks that are read into memory in bits e.g. `max_cache=5.0e8`. Or String. e.g. `max_cache="10MB"` or `max_cache=1GB` defaults to approx 10Mb.
  * `indims::InDims` List of input cube descriptors of type [`InDims`](@ref) for each input data cube.
  * `outdims::OutDims` List of output cube descriptors of type [`OutDims`](@ref) for each output cube.
  * `inplace` does the function write to an output array inplace or return a single value> defaults to `true`
  * `ispar` boolean to determine if parallelisation should be applied, defaults to `true` if workers are available.
  * `showprog` boolean indicating if a ProgressMeter shall be shown
  * `include_loopvars` boolean to indicate if the varoables looped over should be added as function arguments
  * `nthreads` number of threads for the computation, defaults to Threads.nthreads for every worker.
  * `loopchunksize` determines the chunk sizes of variables which are looped over, a dict
  * `kwargs` additional keyword arguments are passed to the inner function

The first argument is always the function to be applied, the second is the input cube or a tuple of input cubes if needed.
