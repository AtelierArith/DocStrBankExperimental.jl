```
lowrankupdowndate!(F::CHOLMOD.Factor, C::Sparse, update::Cint)
```

将 `A` 的 `LDLt` 或 `LLt` 分解 `F` 更新为 `A ± C*C'` 的分解。

如果使用保持稀疏性的分解，即 `L*L' == P*A*P'`，则新因子将是 `L*L' == P*A*P' + C'*C`

`update`：`Cint(1)` 表示 `A + CC'`，`Cint(0)` 表示 `A - CC'`
