```
geev!(jobvl, jobvr, A) -> (W, VL, VR)
```

找到 `A` 的特征系统。如果 `jobvl = N`，则不计算 `A` 的左特征向量。如果 `jobvr = N`，则不计算 `A` 的右特征向量。如果 `jobvl = V` 或 `jobvr = V`，则计算相应的特征向量。返回特征值在 `W` 中，右特征向量在 `VR` 中，左特征向量在 `VL` 中。
