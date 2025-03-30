```
gges!(jobvsl, jobvsr, A, B) -> (A, B, alpha, beta, vsl, vsr)
```

计算 `A` 和 `B` 的广义特征值、广义 Schur 形式、左 Schur 向量（`jobsvl = V`）或右 Schur 向量（`jobvsr = V`）。

广义特征值返回在 `alpha` 和 `beta` 中。左 Schur 向量返回在 `vsl` 中，右 Schur 向量返回在 `vsr` 中。
