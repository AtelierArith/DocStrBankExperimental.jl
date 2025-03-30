```
artifact_meta(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform(),
              pkg_uuid::Union{Base.UUID,Nothing}=nothing)
```

获取关于给定工件（通过名称识别）在给定的 `(Julia)Artifacts.toml` 文件中存储的元数据。如果工件是特定于平台的，请使用 `platform` 选择最合适的映射。如果未找到，返回 `nothing`。

!!! compat "Julia 1.3"
    此函数至少需要 Julia 1.3。

