```
QR <: Factorization
```

以压缩格式存储的 QR 矩阵分解，通常通过 [`qr`](@ref) 获得。如果 $A$ 是一个 `m`×`n` 矩阵，则

$$
A = Q R
$$

其中 $Q$ 是一个正交/单位矩阵，$R$ 是上三角矩阵。矩阵 $Q$ 作为一系列 Householder 反射器 $v_i$ 和系数 $\tau_i$ 存储，其中：

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

迭代分解产生组件 `Q` 和 `R`。

该对象有两个字段：

  * `factors` 是一个 `m`×`n` 矩阵。

      * 上三角部分包含 $R$ 的元素，即 `R = triu(F.factors)` 对于一个 `QR` 对象 `F`。
      * 次对角部分包含以压缩格式存储的反射器 $v_i$，其中 $v_i$ 是矩阵 `V = I + tril(F.factors, -1)` 的第 $i$ 列。
  * `τ` 是一个长度为 `min(m,n)` 的向量，包含系数 $au_i$。
