```
min(x, y, ...)
```

返回参数的最小值，依据 [`isless`](@ref)。如果任何参数为 [`missing`](@ref)，则返回 `missing`。另请参见 [`minimum`](@ref) 函数以从集合中获取最小元素。

# 示例

```jldoctest
julia> min(2, 5, 1)
1

julia> min(4, missing, 6)
missing
```
