```
vect(X...)
```

创建一个 [`Vector`](@ref)，其元素类型由参数的 `promote_typeof` 计算得出，包含参数列表。

# 示例

```jldoctest
julia> a = Base.vect(UInt8(1), 2.5, 1//2)
3-element Vector{Float64}:
 1.0
 2.5
 0.5
```
