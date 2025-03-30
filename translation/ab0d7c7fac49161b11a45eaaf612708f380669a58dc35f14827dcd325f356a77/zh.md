```
summary(io::IO, x)
str = summary(x)
```

打印到流 `io`，或返回字符串 `str`，提供值的简要描述。默认返回 `string(typeof(x))`，例如 [`Int64`](@ref)。

对于数组，返回大小和类型信息的字符串，例如 `10-element Array{Int64,1}`。

# 示例

```jldoctest
julia> summary(1)
"Int64"

julia> summary(zeros(2))
"2-element Vector{Float64}"
```
