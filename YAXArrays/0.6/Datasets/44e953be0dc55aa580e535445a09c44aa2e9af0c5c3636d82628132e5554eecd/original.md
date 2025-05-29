```
savedataset(ds::Dataset; path= "", persist=nothing, overwrite=false, append=false, skeleton=false, backend=:all, driver=backend, max_cache=5e8, writefac=4.0)
```

Saves a Dataset into a file at `path` with the format given by `driver`, i.e., `driver=:netcdf` or `driver=:zarr`.

!!! warning
    `overwrite=true`, deletes ALL your data and it will create a new file.

