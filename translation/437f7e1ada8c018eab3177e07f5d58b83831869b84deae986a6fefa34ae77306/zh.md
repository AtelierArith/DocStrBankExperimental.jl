```
parsefile(f::AbstractString)
parsefile(p::Parser, f::AbstractString)
```

解析文件 `f` 并返回结果表（字典）。在失败时抛出 [`ParserError`](@ref)。

另见 [`TOML.tryparsefile`](@ref)。
