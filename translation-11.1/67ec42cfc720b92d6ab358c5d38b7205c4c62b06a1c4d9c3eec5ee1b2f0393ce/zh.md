```
gebak!(job, side, ilo, ihi, scale, V)
```

将使用 `gebal!` 平衡的矩阵的特征向量 `V` 转换为原始矩阵的未缩放/未排列的特征向量。就地修改 `V`。`side` 可以是 `L`（转换左特征向量）或 `R`（转换右特征向量）。
