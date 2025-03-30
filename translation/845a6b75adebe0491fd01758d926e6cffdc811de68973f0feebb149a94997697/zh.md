```
filter(f)
```

创建一个函数，该函数使用 [`filter`](@ref) 通过函数 `f` 过滤其参数，即一个等价于 `x -> filter(f, x)` 的函数。

返回的函数类型为 `Base.Fix1{typeof(filter)}`，可用于实现专门的方法。

# 示例

```jldoctest
julia> (1, 2, Inf, 4, NaN, 6) |> filter(isfinite)
(1, 2, 4, 6)

julia> map(filter(iseven), [1:3, 2:4, 3:5])
3-element Vector{Vector{Int64}}:
 [2]
 [2, 4]
 [4]
```

!!! compat "Julia 1.9"
    此方法至少需要 Julia 1.9。

