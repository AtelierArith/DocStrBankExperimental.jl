```
OutDims(axisdesc;...)
```

Creates a description of an Output Data Cube for cube operations. Takes a single   or a Vector/Tuple of axes as first argument. Axes can be specified by their   name (String), through an Axis type, or by passing a concrete axis.

  * `axisdesc`: List of input axis names
  * `backend` : specifies the dataset backend to write data to, must be either :auto or a key in `YAXArrayBase.backendlist`
  * `update` : specifies wether the function operates inplace or if an output is returned
  * `artype` : specifies the Array type inside the inner function that is mapped over
  * `chunksize`: A Dict specifying the chunksizes for the output dimensions of the cube, or `:input` to copy chunksizes from input cube axes or `:max` to not chunk the inner dimensions
  * `outtype`: force the output type to a specific type, defaults to `Any` which means that the element type of the first input cube is used
