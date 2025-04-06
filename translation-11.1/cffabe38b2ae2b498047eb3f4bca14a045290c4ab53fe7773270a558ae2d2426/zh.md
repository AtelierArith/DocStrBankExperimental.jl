```
hseqr!(job, compz, ilo, ihi, H, Z) -> (H, Z, w)
```

计算所有特征值和（可选）矩阵的 Schur 分解，该矩阵已被简化为 Hessenberg 形式。如果 `H` 是通过 `gebal!` 平衡的，则 `ilo` 和 `ihi` 是 `gebal!` 的输出。否则，它们应该是 `ilo = 1` 和 `ihi = size(H,2)`。`tau` 包含分解的基本反射器。
