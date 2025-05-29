```
open_mfdataset(files::DD.DimVector{<:AbstractString}; kwargs...)
```

指定された `files` の次元に沿ってデータセットパスのリストを開いて連結します。このメソッドは、一般的なグロブベースのバージョンの open_mfdataset が失敗するか、遅すぎる場合に使用できます。たとえば、`time` 次元に沿って年次 NetCDF ファイルのリストを連結するには、次のようにします。

```julia
files = ["1990.nc","1991.nc","1992.nc"]
open_mfdataset(DD.DimArray(files, YAX.time()))
```

また、連結する次元がまだ存在しない場合は、入力引数で提供された次元が使用されます。

```julia
files = ["a.nc", "b.nc", "c.nc"]
open_mfdataset(DD.DimArray(files, DD.Dim{:NewDim}(["a","b","c"])))
```
