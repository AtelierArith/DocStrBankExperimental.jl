```
stein!(dv, ev_in, w_in, iblock_in, isplit_in)
```

计算对称三对角矩阵的特征向量，其中 `dv` 为对角线，`ev_in` 为副对角线。`w_in` 指定要查找对应特征向量的输入特征值。`iblock_in` 指定与 `w_in` 中特征值对应的子矩阵。`isplit_in` 指定子矩阵块之间的分割点。
