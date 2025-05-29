```
savecube(cube,name::String)
```

Save a [`YAXArray`](@ref) to the `path`.

# Extended Help

The keyword arguments are:

  * `name`:
  * `datasetaxis="Variables"` special treatment of a categorical axis that gets written into separate zarr arrays
  * `max_cache`: The number of bits that are used as cache for the data handling.
  * `backend`: The backend, that is used to save the data. Falls back to searching the backend according to the extension of the path.
  * `driver`: The same setting as `backend`.
  * `overwrite::Bool=false` overwrite cube if it already exists
