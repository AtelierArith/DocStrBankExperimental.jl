```
lowrankupdate!(F::CHOLMOD.Factor, C::AbstractArray)
```

Actualiza una factorización `LDLt` o `LLt` `F` de `A` a una factorización de `A + C*C'`.

Las factorizaciones `LLt` se convierten en `LDLt`.

Véase también [`lowrankupdate`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
