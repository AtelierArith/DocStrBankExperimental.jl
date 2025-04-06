```
endswith(s::AbstractString, suffix::Union{AbstractString,Base.Chars})
```

如果 `s` 以 `suffix` 结尾，则返回 `true`，其中 `suffix` 可以是字符串、字符或字符的元组/向量/集合。如果 `suffix` 是字符的元组/向量/集合，则测试 `s` 的最后一个字符是否属于该集合。

另请参见 [`startswith`](@ref), [`contains`](@ref).

# 示例

```jldoctest
julia> endswith("Sunday", "day")
true
```
