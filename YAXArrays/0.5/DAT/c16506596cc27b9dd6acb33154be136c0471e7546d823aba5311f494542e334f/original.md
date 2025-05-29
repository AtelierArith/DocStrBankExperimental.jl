```
InDims(axisdesc...;...)
```

Creates a description of an Input Data Cube for cube operations. Takes a single   or multiple axis descriptions as first arguments. Alternatively a MovingWindow(@ref) struct can be passed to include   neighbour slices of one or more axes in the computation.    Axes can be specified by their   name (String), through an Axis type, or by passing a concrete axis.

### Keyword arguments

  * `artype` how shall the array be represented in the inner function. Defaults to `Array`, alternatives are `DataFrame` or `AsAxisArray`
  * `filter` define some filter to skip the computation, e.g. when all values are missing. Defaults to   `AllMissing()`, possible values are `AnyMissing()`, `AnyOcean()`, `StdZero()`, `NValid(n)`   (for at least n non-missing elements). It is also possible to provide a custom one-argument function   that takes the array and returns `true` if the compuation shall be skipped and `false` otherwise.
  * `window_oob_value` if one of the input dimensions is a MowingWindow, this value will be used to fill out-of-bounds areas
