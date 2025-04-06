```
artifact_hash(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform())
```

`artifact_meta()` 的薄包装，用于返回指定平台合并的工件的哈希值。如果找不到映射，则返回 `nothing`。

!!! compat "Julia 1.3"
    此函数至少需要 Julia 1.3。

