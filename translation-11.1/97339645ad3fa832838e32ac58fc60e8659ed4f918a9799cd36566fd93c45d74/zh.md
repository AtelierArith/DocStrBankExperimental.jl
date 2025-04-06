```
cis(A::AbstractMatrix)
```

更高效的方法用于平方矩阵 `A` 的 `exp(im*A)`（特别是当 `A` 是 `Hermitian` 或实对称矩阵时）。

另见 [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref)。

!!! compat "Julia 1.7"
    在 Julia 1.7 中添加了对使用 `cis` 处理矩阵的支持。


# 示例

```jldoctest
julia> cis([π 0; 0 π]) ≈ -I
true
```
