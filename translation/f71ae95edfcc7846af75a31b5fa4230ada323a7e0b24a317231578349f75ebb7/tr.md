```
lowrankdowndate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

Bir `LDLt` Faktörizasyonu `A + C*C'` için, `A`'nın `LDLt` veya `LLt` faktörizasyonu `F` verildiğinde.

Dönen faktör her zaman bir `LDLt` faktörizasyonudur.

Ayrıca bkz. [`lowrankdowndate!`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref).
