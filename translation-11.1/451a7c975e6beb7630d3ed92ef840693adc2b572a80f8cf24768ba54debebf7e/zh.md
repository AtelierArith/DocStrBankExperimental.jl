```
axes(A)
```

返回数组 `A` 的有效索引元组。

另请参见: [`size`](@ref), [`keys`](@ref), [`eachindex`](@ref)。

# 示例

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A)
(Base.OneTo(5), Base.OneTo(6), Base.OneTo(7))
```
