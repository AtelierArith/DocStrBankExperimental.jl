```
lowrankdowndate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

Obtiene una factorización `LDLt` de `A + C*C'` dada una factorización `LDLt` o `LLt` `F` de `A`.

El factor devuelto es siempre una factorización `LDLt`.

Véase también [`lowrankdowndate!`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref).
