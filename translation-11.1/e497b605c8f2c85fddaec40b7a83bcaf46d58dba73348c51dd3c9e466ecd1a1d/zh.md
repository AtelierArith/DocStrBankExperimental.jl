```
uppercasefirst(s::AbstractString) -> String
```

返回 `s`，其首个字符转换为大写（在技术上是 Unicode 的“标题大小”）。另请参见 [`titlecase`](@ref) 以将 `s` 中每个单词的首个字符大写。

另请参见 [`lowercasefirst`](@ref)，[`uppercase`](@ref)，[`lowercase`](@ref)，[`titlecase`](@ref)。

# 示例

```jldoctest
julia> uppercasefirst("python")
"Python"
```
