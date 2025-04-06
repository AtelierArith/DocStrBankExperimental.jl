```
getrf!(A, ipiv) -> (A, ipiv, info)
```

计算 `A` 的带主元的 `LU` 分解，`A = LU`。`ipiv` 包含主元信息，`info` 是一个代码，指示成功（`info = 0`）、`U` 中的奇异值（`info = i`，在这种情况下 `U[i,i]` 是奇异的），或错误代码（`info < 0`）。
