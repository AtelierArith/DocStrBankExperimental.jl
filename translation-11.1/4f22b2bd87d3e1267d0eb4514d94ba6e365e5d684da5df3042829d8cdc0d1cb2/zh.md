```
pttrs!(D, E, B)
```

求解正定三对角矩阵 `A` 的方程 `A * X = B`，其中对角线为 `D`，副对角线为 `E`，在使用 `pttrf!` 计算 `A` 的 LDLt 分解后。`B` 被覆盖为解 `X`。
