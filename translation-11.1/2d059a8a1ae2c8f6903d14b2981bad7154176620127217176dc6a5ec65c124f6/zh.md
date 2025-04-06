```
startswith(s::AbstractString, prefix::Union{AbstractString,Base.Chars})
```

如果 `s` 以 `prefix` 开头，则返回 `true`，其中 `prefix` 可以是字符串、字符或字符的元组/向量/集合。如果 `prefix` 是字符的元组/向量/集合，则测试 `s` 的第一个字符是否属于该集合。

另请参见 [`endswith`](@ref), [`contains`](@ref).

# 示例

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
