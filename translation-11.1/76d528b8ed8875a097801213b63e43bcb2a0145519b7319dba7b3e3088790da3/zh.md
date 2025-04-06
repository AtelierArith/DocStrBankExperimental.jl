```
stebz!(range, order, vl, vu, il, iu, abstol, dv, ev) -> (dv, iblock, isplit)
```

计算对称三对角矩阵的特征值，其中 `dv` 为对角线，`ev` 为非对角线。如果 `range = A`，则找到所有特征值。如果 `range = V`，则找到半开区间 `(vl, vu]` 中的特征值。如果 `range = I`，则找到索引在 `il` 和 `iu` 之间的特征值。如果 `order = B`，特征值在一个块内排序。如果 `order = E`，则在所有块之间排序。`abstol` 可以设置为收敛的容差。
