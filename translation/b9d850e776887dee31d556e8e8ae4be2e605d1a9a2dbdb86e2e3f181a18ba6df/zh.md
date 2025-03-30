```
QRCompactWY <: Factorization
```

一种以紧凑块格式存储的 QR 矩阵分解，通常通过 [`qr`](@ref) 获得。如果 $A$ 是一个 `m`×`n` 矩阵，则

$$
A = Q R
$$

其中 $Q$ 是一个正交/单位矩阵，$R$ 是上三角矩阵。它与 [`QR`](@ref) 格式类似，除了正交/单位矩阵 $Q$ 以 *Compact WY* 格式存储 [^Schreiber1989]。对于块大小 $n_b$，它被存储为一个 `m`×`n` 的下梯形矩阵 $V$ 和一个矩阵 $T = (T_1 \; T_2 \; ... \; T_{b-1} \; T_b')$，由 $b = \lceil \min(m,n) / n_b \rceil$ 个大小为 $n_b$×$n_b$ 的上三角矩阵 $T_j$ ($j = 1, ..., b-1$) 和一个上梯形的 $n_b$×$\min(m,n) - (b-1) n_b$ 矩阵 $T_b'$ ($j=b$) 组成，其上方的平方部分用 $T_b$ 表示，满足

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T)
= \prod_{j=1}^{b} (I - V_j T_j V_j^T)
$$

其中 $v_i$ 是 $V$ 的第 $i$ 列，$\tau_i$ 是 `[diag(T_1); diag(T_2); …; diag(T_b)]` 的第 $i$ 个元素，$(V_1 \; V_2 \; ... \; V_b)$ 是 $V$ 的左 `m`×`min(m, n)` 块。当使用 [`qr`](@ref) 构造时，块大小由 $n_b = \min(m, n, 36)$ 给出。

迭代分解产生组件 `Q` 和 `R`。

该对象有两个字段：

  * `factors`，如同 [`QR`](@ref) 类型，是一个 `m`×`n` 矩阵。

      * 上三角部分包含 $R$ 的元素，即 `R = triu(F.factors)` 对于一个 `QR` 对象 `F`。
      * 次对角部分包含反射器 $v_i$，以打包格式存储，使得 `V = I + tril(F.factors, -1)`。
  * `T` 是一个 $n_b$×$\min(m,n)$ 矩阵，如上所述。每个三角矩阵 $T_j$ 的次对角元素被忽略。

!!! note
    此格式不应与较旧的 *WY* 表示法混淆 [^Bischof1987]。


[^Bischof1987]: C Bischof 和 C Van Loan, "The WY representation for products of Householder matrices", SIAM J Sci Stat Comput 8 (1987), s2-s13. [doi:10.1137/0908009](https://doi.org/10.1137/0908009)

[^Schreiber1989]: R Schreiber 和 C Van Loan, "A storage-efficient WY representation for products of Householder transformations", SIAM J Sci Stat Comput 10 (1989), 53-57. [doi:10.1137/0910005](https://doi.org/10.1137/0910005)
