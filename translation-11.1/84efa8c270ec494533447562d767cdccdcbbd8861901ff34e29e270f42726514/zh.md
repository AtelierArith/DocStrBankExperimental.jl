```
ggev3!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

使用分块算法查找 `A` 和 `B` 的广义特征分解。如果 `jobvl = N`，则不计算左特征向量。如果 `jobvr = N`，则不计算右特征向量。如果 `jobvl = V` 或 `jobvr = V`，则计算相应的特征向量。此函数需要 LAPACK 3.6.0。
