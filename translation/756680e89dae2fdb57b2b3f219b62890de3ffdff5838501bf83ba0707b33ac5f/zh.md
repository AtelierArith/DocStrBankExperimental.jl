```
ndims(A::AbstractArray) -> Integer
```

返回 `A` 的维数。

另见：[`size`](@ref), [`axes`](@ref)。

# 示例

```jldoctest
julia> A = fill(1, (3,4,5));

julia> ndims(A)
3
```
