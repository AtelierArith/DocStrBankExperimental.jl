```
Parser()
```

用于创建 TOML `Parser` 的构造函数。请注意，在大多数情况下，您不需要显式创建 `Parser`，而是直接使用 [`TOML.parsefile`](@ref) 或 [`TOML.parse`](@ref)。然而，使用显式解析器将重用一些内部数据结构，这在解析大量小文件时对性能是有益的。
