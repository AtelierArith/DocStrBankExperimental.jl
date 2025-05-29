```
savedataset(ds::Dataset; path= "", persist=nothing, overwrite=false, append=false, skeleton=false, backend=:all, driver=backend, max_cache=5e8, writefac=4.0)
```

指定された`driver`によって、`path`にファイルとしてDatasetを保存します。すなわち、`driver=:netcdf`または`driver=:zarr`です。

!!! warning
    `overwrite=true`の場合、すべてのデータが削除され、新しいファイルが作成されます。

