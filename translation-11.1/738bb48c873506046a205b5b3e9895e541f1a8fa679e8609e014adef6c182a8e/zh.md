```
QRPivoted <: Factorization
```

带列主元的 QR 矩阵分解，采用压缩格式，通常从 [`qr`](@ref) 获得。如果 $A$ 是一个 `m`×`n` 矩阵，则

$$
A P = Q R
$$

其中 $P$ 是一个置换矩阵，$Q$ 是一个正交/单位矩阵，$R$ 是上三角矩阵。矩阵 $Q$ 作为一系列 Householder 反射器存储：

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

迭代分解产生组件 `Q`、`R` 和 `p`。

该对象有三个字段：

  * `factors` 是一个 `m`×`n` 矩阵。

      * 上三角部分包含 $R$ 的元素，即 `R = triu(F.factors)` 对于一个 `QR` 对象 `F`。
      * 次对角部分包含反射器 $v_i$，以压缩格式存储，其中 $v_i$ 是矩阵 `V = I + tril(F.factors, -1)` 的第 $i$ 列。
  * `τ` 是一个长度为 `min(m,n)` 的向量，包含系数 $au_i$。
  * `jpvt` 是一个长度为 `n` 的整数向量，对应于置换 $P$。
