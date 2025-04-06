```
GitConfig(path::AbstractString, level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP, force::Bool=false)
```

`path` üzerindeki dosyadan yapılandırma bilgilerini yükleyerek yeni bir `GitConfig` oluşturur. `level`, `repo` ve `force` seçenekleri hakkında daha fazla bilgi için [`addfile`](@ref) bölümüne bakın.
