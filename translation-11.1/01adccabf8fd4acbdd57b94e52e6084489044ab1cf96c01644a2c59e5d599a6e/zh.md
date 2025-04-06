```
split(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
split(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

将 `str` 按照分隔符 `dlm` 的出现位置拆分为一个子字符串数组。 `dlm` 可以是 [`findnext`](@ref) 的第一个参数允许的任何格式（即作为字符串、正则表达式或函数），或者是单个字符或字符集合。

如果省略 `dlm`，则默认为 [`isspace`](@ref)。

可选的关键字参数有：

  * `limit`：结果的最大大小。 `limit=0` 表示没有最大值（默认）
  * `keepempty`：是否在结果中保留空字段。 默认情况下，如果没有 `dlm` 参数，则为 `false`，如果有 `dlm` 参数，则为 `true`。

另请参见 [`rsplit`](@ref)，[`eachsplit`](@ref)。

# 示例

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> split(a, ".")
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
