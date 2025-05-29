```
open_mfdataset(files::DD.DimVector{<:AbstractString}; kwargs...)
```

Opens and concatenates a list of dataset paths along the dimension specified in `files`.  This method can be used when the generic glob-based version of open_mfdataset fails or is too slow.  For example, to concatenate a list of annual NetCDF files along the `time` dimension,  one can use:

```julia
files = ["1990.nc","1991.nc","1992.nc"]
open_mfdataset(DD.DimArray(files, YAX.time()))
```

alternatively, if the dimension to concatenate along does not exist yet, the  dimension provided in the input arg is used:

```julia
files = ["a.nc", "b.nc", "c.nc"]
open_mfdataset(DD.DimArray(files, DD.Dim{:NewDim}(["a","b","c"])))
```
