```
eachrsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachrsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

返回一个迭代器，迭代 `str` 的 `SubString`，当在分隔符 `dlm` 上拆分时生成，并以相反的顺序（从右到左）返回。`dlm` 可以是 [`findprev`](@ref) 的第一个参数允许的任何格式（即字符串、单个字符或函数），或字符集合。

如果省略 `dlm`，则默认为 [`isspace`](@ref)，并且 `keepempty` 默认为 `false`。

可选的关键字参数有：

  * 如果 `limit > 0`，迭代器最多将在返回其余未拆分的字符串之前拆分 `limit - 1` 次。`limit < 1` 意味着没有拆分限制（默认）。
  * `keepempty`：在迭代时是否应返回空字段。默认情况下，如果没有 `dlm` 参数，则为 `false`，如果有 `dlm` 参数，则为 `true`。

请注意，与 [`split`](@ref)、[`rsplit`](@ref) 和 [`eachsplit`](@ref) 不同，此函数按输入中出现的顺序从右到左迭代子字符串。

另请参见 [`eachsplit`](@ref)、[`rsplit`](@ref)。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


# 示例

```jldoctest
julia> a = "Ma.r.ch";

julia> collect(eachrsplit(a, ".")) == ["ch", "r", "Ma"]
true

julia> collect(eachrsplit(a, "."; limit=2)) == ["ch", "Ma.r"]
true
```
