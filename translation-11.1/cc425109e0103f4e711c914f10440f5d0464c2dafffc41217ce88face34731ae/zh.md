```
condskeel(M, [x, p::Real=Inf])
```

$$
\kappa_S(M, p) = \left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \right\Vert_p \\
\kappa_S(M, x, p) = \frac{\left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \left\vert x \right\vert \right\Vert_p}{\left \Vert x \right \Vert_p}
$$

矩阵 `M` 的 Skeel 条件数 $\kappa_S$，可选地与向量 `x` 相关，使用算子 `p`-范数计算。$\left\vert M \right\vert$ 表示矩阵 $M$ 的（逐元素）绝对值矩阵；$\left\vert M \right\vert_{ij} = \left\vert M_{ij} \right\vert$。`p` 的有效值为 `1`、`2` 和 `Inf`（默认）。

这个量在文献中也被称为 Bauer 条件数、相对条件数或逐分量相对条件数。
