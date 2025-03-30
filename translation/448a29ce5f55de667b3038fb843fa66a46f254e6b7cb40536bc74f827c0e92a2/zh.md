```
parse(x::Union{AbstractString, IO})
parse(p::Parser, x::Union{AbstractString, IO})
```

解析字符串或流 `x`，并返回结果表（字典）。在失败时抛出 [`ParserError`](@ref)。

另见 [`TOML.tryparse`](@ref)。
