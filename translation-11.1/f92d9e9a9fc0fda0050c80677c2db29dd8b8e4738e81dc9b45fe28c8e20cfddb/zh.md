```
tryparsefile(f::AbstractString)
tryparsefile(p::Parser, f::AbstractString)
```

解析文件 `f` 并返回结果表（字典）。在失败时返回一个 [`ParserError`](@ref)。

另见 [`TOML.parsefile`](@ref)。
