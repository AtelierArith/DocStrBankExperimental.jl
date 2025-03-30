```
eachsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

在分隔符 `dlm` 出现的地方拆分 `str`，并返回一个子字符串的迭代器。`dlm` 可以是 [`findnext`](@ref) 的第一个参数允许的任何格式（即作为字符串、正则表达式或函数），或者作为单个字符或字符集合。

如果省略 `dlm`，则默认为 [`isspace`](@ref)。

可选的关键字参数有：

  * `limit`：结果的最大大小。`limit=0` 表示没有最大值（默认）
  * `keepempty`：是否应在结果中保留空字段。没有 `dlm` 参数时默认是 `false`，有 `dlm` 参数时默认是 `true`。

另见 [`split`](@ref)。

!!! compat "Julia 1.8"
    `eachsplit` 函数需要至少 Julia 1.8。


# 示例

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> b = eachsplit(a, ".")
Base.SplitIterator{String, String}("Ma.rch", ".", 0, true)

julia> collect(b)
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
