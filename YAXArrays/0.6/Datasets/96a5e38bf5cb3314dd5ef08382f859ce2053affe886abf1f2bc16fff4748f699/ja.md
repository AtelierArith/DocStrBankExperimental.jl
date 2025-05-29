```
open_dataset(g; skip_keys=(), driver=:all)
```

指定された`driver`を使用して、`g`のデータセットを開きます。デフォルトのドライバーは、利用可能なドライバーを検索し、ファイル名の拡張子から使用可能なドライバーを検出しようとします。

### キーワード引数

  * `skip_keys`はシンボルとして渡されます。すなわち、`skip_keys = (:a, :b)`
  * `driver=:all`、一般的なオプションは`:netcdf`または`:zarr`です。

例:

```julia
ds = open_dataset(f, driver=:zarr, skip_keys = (:c,))
```
