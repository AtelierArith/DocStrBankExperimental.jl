```
lowrankdowndate!(F::CHOLMOD.Factor, C::AbstractArray)
```

将 `A` 的 `LDLt` 或 `LLt` 分解 `F` 更新为 `A - C*C'` 的分解。

`LLt` 分解会转换为 `LDLt`。

另见 [`lowrankdowndate`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref).
