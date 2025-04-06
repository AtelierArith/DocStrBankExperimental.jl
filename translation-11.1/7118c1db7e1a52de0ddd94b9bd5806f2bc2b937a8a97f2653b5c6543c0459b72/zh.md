```
geevx!(balanc, jobvl, jobvr, sense, A) -> (A, w, VL, VR, ilo, ihi, scale, abnrm, rconde, rcondv)
```

找到具有矩阵平衡的 `A` 的特征系统。如果 `jobvl = N`，则不计算 `A` 的左特征向量。如果 `jobvr = N`，则不计算 `A` 的右特征向量。如果 `jobvl = V` 或 `jobvr = V`，则计算相应的特征向量。如果 `balanc = N`，则不执行平衡。如果 `balanc = P`，则 `A` 被置换但不缩放。如果 `balanc = S`，则 `A` 被缩放但不置换。如果 `balanc = B`，则 `A` 被置换并缩放。如果 `sense = N`，则不计算倒数条件数。如果 `sense = E`，则仅计算特征值的倒数条件数。如果 `sense = V`，则仅计算右特征向量的倒数条件数。如果 `sense = B`，则计算右特征向量和特征向量的倒数条件数。如果 `sense = E,B`，则必须计算右和左特征向量。
