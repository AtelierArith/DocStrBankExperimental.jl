```
lowrankupdate(F::CHOLMOD.Factor, C::AbstractArray) -> FF::CHOLMOD.Factor
```

Erhalten Sie eine `LDLt`-Faktorisierung von `A + C*C'`, gegeben eine `LDLt`- oder `LLt`-Faktorisierung `F` von `A`.

Der zurückgegebene Faktor ist immer eine `LDLt`-Faktorisierung.

Siehe auch [`lowrankupdate!`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
