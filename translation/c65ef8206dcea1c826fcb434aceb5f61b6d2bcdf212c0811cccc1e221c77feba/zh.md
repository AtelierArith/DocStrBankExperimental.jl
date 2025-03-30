```
gees!(jobvs, A) -> (A, vs, w)
```

计算矩阵 `A` 的特征值（`jobvs = N`）或特征值和 Schur 向量（`jobvs = V`）。`A` 被其 Schur 形式覆盖。

返回 `A`、包含 Schur 向量的 `vs` 和包含特征值的 `w`。
