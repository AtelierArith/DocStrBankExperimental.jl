```
lowrankdowndate!(F::CHOLMOD.Factor, C::AbstractArray)
```

Bir `LDLt` veya `LLt` Faktörizasyonu `F`'yi `A - C*C'`'nin bir faktörizasyonuna günceller.

`LLt` faktörizasyonları `LDLt`'ye dönüştürülür.

Ayrıca bkz. [`lowrankdowndate`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref).
