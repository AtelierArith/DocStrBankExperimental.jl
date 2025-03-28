```
lowrankdowndate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

Erhalte eine `LDLt`-Faktorisierung von `A + C*C'`, gegeben eine `LDLt`- oder `LLt`-Faktorisierung `F` von `A`.

Der zurückgegebene Faktor ist immer eine `LDLt`-Faktorisierung.

Siehe auch [`lowrankdowndate!`](@ref), [`lowrankupdate`](@ref), [`lowrankupdate!`](@ref).
