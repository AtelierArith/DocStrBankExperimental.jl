```
orgrq!(A, tau, k = length(tau))
```

显式地找到在对 `A` 调用 `gerqf!` 之后的 `RQ` 分解的矩阵 `Q`。使用 `gerqf!` 的输出。`A` 被 `Q` 覆盖。
