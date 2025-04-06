```
gecon!(normtype, A, anorm)
```

找到矩阵 `A` 的倒数条件数。如果 `normtype = I`，则条件数在无穷范数中找到。如果 `normtype = O` 或 `1`，则条件数在一范数中找到。`A` 必须是 `getrf!` 的结果，`anorm` 是 `A` 在相关范数中的范数。
