```
lowrankupdate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

获取给定 `A` 的 `LDLt` 或 `LLt` 分解 `F` 的 `A + C*C'` 的 `LDLt` 分解。

返回的因子始终是 `LDLt` 分解。

另见 [`lowrankupdate!`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
