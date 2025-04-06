```
find_artifacts_toml(path::String)
```

给定一个 `.jl` 文件的路径（例如，在宏上下文中由 `__source__.file` 返回的路径），查找包含项目中的 `(Julia)Artifacts.toml`（如果存在），否则返回 `nothing`。

!!! compat "Julia 1.3"
    此函数至少需要 Julia 1.3。

