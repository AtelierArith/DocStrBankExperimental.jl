```
reduce(f, A::AbstractArray; dims=:, [init])
```

沿着 `A` 的维度减少 2-参数函数 `f`。`dims` 是一个指定要减少的维度的向量，关键字参数 `init` 是在减少中使用的初始值。对于 `+`、`*`、`max` 和 `min`，`init` 参数是可选的。

减少的结合性依赖于实现；如果您需要特定的结合性，例如从左到右，您应该编写自己的循环或考虑使用 [`foldl`](@ref) 或 [`foldr`](@ref)。有关 [`reduce`](@ref) 的文档，请参见。

# 示例

```jldoctest
julia> a = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reduce(max, a, dims=2)
4×1 Matrix{Int64}:
 13
 14
 15
 16

julia> reduce(max, a, dims=1)
1×4 Matrix{Int64}:
 4  8  12  16
```
