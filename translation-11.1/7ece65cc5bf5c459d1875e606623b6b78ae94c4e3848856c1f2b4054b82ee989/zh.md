```
svd(A, B) -> GeneralizedSVD
```

计算 `A` 和 `B` 的广义 SVD，返回一个 `GeneralizedSVD` 分解对象 `F`，使得 `[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'`

  * `U` 是一个 M-by-M 的正交矩阵，
  * `V` 是一个 P-by-P 的正交矩阵，
  * `Q` 是一个 N-by-N 的正交矩阵，
  * `D1` 是一个 M-by-(K+L) 的对角矩阵，前 K 个元素为 1，
  * `D2` 是一个 P-by-(K+L) 的矩阵，其右上角的 L-by-L 块是对角的，
  * `R0` 是一个 (K+L)-by-N 的矩阵，其最右侧的 (K+L)-by-(K+L) 块是非奇异的上三角块，

`K+L` 是矩阵 `[A; B]` 的有效数值秩。

迭代分解产生组件 `U`、`V`、`Q`、`D1`、`D2` 和 `R0`。

广义 SVD 用于应用场景，例如当人们想比较 `A` 和 `B` 各自的贡献时，如人类与酵母基因组，或信号与噪声，或聚类之间与聚类内部的比较。（参见 Edelman 和 Wang 的讨论：https://arxiv.org/abs/1901.00485）

它将 `[A; B]` 分解为 `[UC; VS]H`，其中 `[UC; VS]` 是 `[A; B]` 列空间的自然正交基，`H = RQ'` 是 `[A;B]` 行空间的自然非正交基，其中顶部行最密切归因于 `A` 矩阵，底部行归因于 `B` 矩阵。多余弦/正弦矩阵 `C` 和 `S` 提供了 `A` 与 `B` 的多重度量，而 `U` 和 `V` 提供了这些度量的方向。

# 示例

```jldoctest
julia> A = randn(3,2); B=randn(4,2);

julia> F = svd(A, B);

julia> U,V,Q,C,S,R = F;

julia> H = R*Q';

julia> [A; B] ≈ [U*C; V*S]*H
true

julia> [A; B] ≈ [F.U*F.D1; F.V*F.D2]*F.R0*F.Q'
true

julia> Uonly, = svd(A,B);

julia> U == Uonly
true
```
