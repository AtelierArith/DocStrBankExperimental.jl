```
ldiv!(Y, A, B) -> Y
```

计算 `A \ B` 并将结果存储在 `Y` 中，返回结果。

参数 `A` *不* 应该是一个矩阵。相反，它应该是一个分解对象（例如，由 [`factorize`](@ref) 或 [`cholesky`](@ref) 生成）。这样做的原因是，分解本身既昂贵又通常会分配内存（尽管也可以通过例如 [`lu!`](@ref) 进行就地操作），而在性能关键的情况下，通常需要对 `A` 的分解进行细粒度控制。

!!! note
    某些结构化矩阵类型，例如 `Diagonal` 和 `UpperTriangular`，是被允许的，因为它们已经处于分解形式


# 示例

```jldoctest
julia> A = [1 2.2 4; 3.1 0.2 3; 4 1 2];

julia> X = [1; 2.5; 3];

julia> Y = zero(X);

julia> ldiv!(Y, qr(A), X);

julia> Y ≈ A\X
true
```
