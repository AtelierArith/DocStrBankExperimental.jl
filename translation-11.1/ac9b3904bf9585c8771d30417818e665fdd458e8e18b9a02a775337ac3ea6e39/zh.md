```
parentindices(A)
```

返回与视图 `A` 对应的 [`parent`](@ref) 中的索引。

# 示例

```jldoctest
julia> A = [1 2; 3 4];

julia> V = view(A, 1, :)
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2

julia> parentindices(V)
(1, Base.Slice(Base.OneTo(2)))
```
