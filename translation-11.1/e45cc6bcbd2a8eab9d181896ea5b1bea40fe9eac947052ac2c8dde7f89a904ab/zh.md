```
opnorm(A::Adjoint{<:Any,<:AbstractVector}, q::Real=2)
opnorm(A::Transpose{<:Any,<:AbstractVector}, q::Real=2)
```

对于 Adjoint/Transpose 包装的向量，返回 `A` 的算子 $q$-范数，这等同于值为 `p = q/(q-1)` 的 `p`-范数。在 `p = q = 2` 时它们是一致的。使用 [`norm`](@ref) 计算 `A` 作为向量的 `p` 范数。

向量空间与其对偶之间的范数差异是为了保持对偶性与点积之间的关系，结果与 `1 × n` 矩阵的算子 `p`-范数一致。

# 示例

```jldoctest
julia> v = [1; im];

julia> vc = v';

julia> opnorm(vc, 1)
1.0

julia> norm(vc, 1)
2.0

julia> norm(v, 1)
2.0

julia> opnorm(vc, 2)
1.4142135623730951

julia> norm(vc, 2)
1.4142135623730951

julia> norm(v, 2)
1.4142135623730951

julia> opnorm(vc, Inf)
2.0

julia> norm(vc, Inf)
1.0

julia> norm(v, Inf)
1.0
```
