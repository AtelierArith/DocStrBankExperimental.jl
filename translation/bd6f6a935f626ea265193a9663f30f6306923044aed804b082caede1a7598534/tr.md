```
lowrankupdate!(F::CHOLMOD.Factor, C::AbstractArray)
```

Bir `LDLt` veya `LLt` Faktörizasyonu `F`'yi `A + C*C'`'nin bir faktörizasyonuna güncelleyin.

`LLt` faktörizasyonları `LDLt`'ye dönüştürülür.

Ayrıca bkz. [`lowrankupdate`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
