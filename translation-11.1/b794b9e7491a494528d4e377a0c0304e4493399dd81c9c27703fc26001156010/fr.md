```
lowrankupdate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

Obtenez une factorisation `LDLt` de `A + C*C'` donnée une factorisation `LDLt` ou `LLt` `F` de `A`.

Le facteur retourné est toujours une factorisation `LDLt`.

Voir aussi [`lowrankupdate!`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
