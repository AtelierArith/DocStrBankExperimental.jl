```
trevc!(side, howmny, select, T, VL = similar(T), VR = similar(T))
```

查找上三角矩阵 `T` 的特征系统。如果 `side = R`，则计算右特征向量。如果 `side = L`，则计算左特征向量。如果 `side = B`，则计算两组特征向量。如果 `howmny = A`，则找到所有特征向量。如果 `howmny = B`，则找到所有特征向量并使用 `VL` 和 `VR` 进行反变换。如果 `howmny = S`，则仅计算与 `select` 中的值对应的特征向量。
