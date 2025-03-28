```
lowrankupdate!(F::CHOLMOD.Factor, C::AbstractArray)
```

Met à jour une factorisation `LDLt` ou `LLt` `F` de `A` à une factorisation de `A + C*C'`.

Les factorizations `LLt` sont converties en `LDLt`.

Voir aussi [`lowrankupdate`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
