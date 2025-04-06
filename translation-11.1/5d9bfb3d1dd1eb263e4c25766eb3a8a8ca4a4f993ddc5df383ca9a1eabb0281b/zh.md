```
stegr!(jobz, range, dv, ev, vl, vu, il, iu) -> (w, Z)
```

计算对称三对角矩阵的特征值（`jobz = N`）或特征值和特征向量（`jobz = V`），其中 `dv` 为对角线，`ev` 为非对角线。如果 `range = A`，则找到所有特征值。如果 `range = V`，则找到半开区间 `(vl, vu]` 中的特征值。如果 `range = I`，则找到索引在 `il` 和 `iu` 之间的特征值。特征值返回在 `w` 中，特征向量返回在 `Z` 中。
