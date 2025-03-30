```
addfile(cfg::GitConfig, path::AbstractString,
        level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP,
        repo::Union{GitRepo, Nothing} = nothing,
        force::Bool=false)
```

Mevcut `GitConfig` `cfg`'ye `path` konumundaki mevcut bir git yapılandırma dosyası ekleyin. Dosya mevcut değilse, oluşturulacaktır.

  * `level`, git yapılandırma öncelik seviyesini ayarlar ve

[`Consts.GIT_CONFIG`](@ref) tarafından belirlenir.

  * `repo`, koşullu içeriklerin ayrıştırılmasına izin vermek için isteğe bağlı bir depodur.
  * `force` `false` ise ve verilen öncelik seviyesi için bir yapılandırma zaten mevcutsa,

`addfile` hata verecektir. `force` `true` ise, mevcut yapılandırma `path` konumundaki dosyadaki ile değiştirilecektir.
