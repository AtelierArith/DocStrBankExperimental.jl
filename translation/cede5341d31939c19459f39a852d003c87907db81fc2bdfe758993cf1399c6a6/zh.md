```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

计算 `A` 的奇异值分解（SVD）并返回一个 `SVD` 对象。

`U`、`S`、`V` 和 `Vt` 可以通过因式分解 `F` 获取，使用 `F.U`、`F.S`、`F.V` 和 `F.Vt`，使得 `A = U * Diagonal(S) * Vt`。该算法生成 `Vt`，因此提取 `Vt` 比提取 `V` 更高效。`S` 中的奇异值按降序排列。

迭代分解会产生组件 `U`、`S` 和 `V`。

如果 `full = false`（默认），则返回“瘦”SVD。对于一个 $M \times N$ 矩阵 `A`，在完整因式分解中 `U` 是 $M \times M$，而 `V` 是 $N \times N$，而在瘦因式分解中 `U` 是 $M \times K$，`V` 是 $N \times K$，其中 $K = \min(M,N)$ 是奇异值的数量。

如果 `alg = DivideAndConquer()`，则使用分治算法来计算 SVD。另一个（通常较慢但更准确）选项是 `alg = QRIteration()`。

!!! compat "Julia 1.3"
    `alg` 关键字参数需要 Julia 1.3 或更高版本。


# 示例

```jldoctest
julia> A = rand(4,3);

julia> F = svd(A); # 存储因式分解对象

julia> A ≈ F.U * Diagonal(F.S) * F.Vt
true

julia> U, S, V = F; # 通过迭代解构

julia> A ≈ U * Diagonal(S) * V'
true

julia> Uonly, = svd(A); # 仅存储 U

julia> Uonly == U
true
```
