```
cubefittable(tab,o,fitsym;post=getpostfunction(o),kwargs...)
```

Executes [`fittable`](@ref) on the [`CubeTable`](@ref) `tab` with the (Weighted-)OnlineStat `o`, looping through the values specified by `fitsym`. Finally, writes the results from the `TableAggregator` to an output data cube.
