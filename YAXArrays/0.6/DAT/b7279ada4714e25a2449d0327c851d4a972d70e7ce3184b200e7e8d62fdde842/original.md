```
mapCube(fun, cube, addargs...;kwargs...)
```

Map a given function `fun` over slices of all cubes of the dataset `ds`.  Use InDims to discribe the input dimensions and OutDims to describe the output dimensions of the function.

For Datasets, only one output cube can be specified. In contrast to the mapCube function for cubes, additional arguments for the inner function should be set as keyword arguments.

For the specific keyword arguments see the docstring of the mapCube function for cubes.
