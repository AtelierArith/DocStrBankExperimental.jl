```
artifact_exists(hash::SHA1; honor_overrides::Bool=true)
```

返回给定的工件（通过其 sha1 git 树哈希标识）是否存在于磁盘上。请注意，给定的工件可能存在于多个位置（例如，在多个仓库中）。

!!! compat "Julia 1.3"
    此函数至少需要 Julia 1.3。

