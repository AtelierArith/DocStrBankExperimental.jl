```
artifact_path(hash::SHA1; honor_overrides::Bool=true)
```

给定一个工件（由SHA1 git树哈希标识），返回其安装路径。如果工件不存在，则返回它将被安装到的位置。

!!! compat "Julia 1.3"
    此函数至少需要Julia 1.3。

