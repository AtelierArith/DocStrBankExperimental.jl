```
lowrankdowndate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

给定 `A` 的 `LDLt` 或 `LLt` 分解 `F`，获取 `A + C*C'` 的 `LDLt` 分解。

返回的因子始终是 `LDLt` 分解。

另见 [`lowrankdowndate!`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref).
