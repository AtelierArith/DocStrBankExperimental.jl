```
gels!(trans, A, B) -> (F, B, ssr)
```

求解线性方程 `A * X = B`、`transpose(A) * X = B` 或 `adjoint(A) * X = B`，使用 QR 或 LQ 分解。就地修改矩阵/向量 `B` 以得到解。`A` 被其 `QR` 或 `LQ` 分解覆盖。`trans` 可以是 `N`（不修改）、`T`（转置）或 `C`（共轭转置）。`gels!` 寻找最小范数/最小二乘解。`A` 可能是欠定或超定的。解返回在 `B` 中。
