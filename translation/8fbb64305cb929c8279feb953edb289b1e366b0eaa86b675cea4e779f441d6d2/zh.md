```
getrf!(A) -> (A, ipiv, info)
```

计算 `A` 的带主元的 `LU` 分解，`A = LU`。

返回修改后的 `A`、主元信息 `ipiv` 和一个 `info` 代码，指示成功（`info = 0`）、`U` 中的奇异值（`info = i`，在这种情况下 `U[i,i]` 是奇异的）或错误代码（`info < 0`）。
