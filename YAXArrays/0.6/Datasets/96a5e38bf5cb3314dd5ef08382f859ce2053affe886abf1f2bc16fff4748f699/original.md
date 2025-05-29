```
open_dataset(g; skip_keys=(), driver=:all)
```

Open the dataset at `g` with the given `driver`. The default driver will search for available drivers and tries to detect the useable driver from the filename extension.

### Keyword arguments

  * `skip_keys` are passed as symbols, i.e., `skip_keys = (:a, :b)`
  * `driver=:all`, common options are `:netcdf` or `:zarr`.

Example:

```julia
ds = open_dataset(f, driver=:zarr, skip_keys = (:c,))
```
