```
max(x, y, ...)
```

返回参数的最大值，依据 [`isless`](@ref)。如果任何参数为 [`missing`](@ref)，则返回 `missing`。另请参见 [`maximum`](@ref) 函数以从集合中获取最大元素。

# 示例

```jldoctest
julia> max(2, 5, 1)
5

julia> max(5, missing, 6)
missing
```
