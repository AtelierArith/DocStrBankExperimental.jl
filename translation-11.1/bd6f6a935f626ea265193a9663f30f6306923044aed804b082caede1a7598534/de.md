```
lowrankupdate!(F::CHOLMOD.Factor, C::AbstractArray)
```

Aktualisiert eine `LDLt`- oder `LLt`-Faktorisierung `F` von `A` zu einer Faktorisierung von `A + C*C'`.

`LLt`-Faktorisierungen werden in `LDLt` umgewandelt.

Siehe auch [`lowrankupdate`](@ref), [`lowrankdowndate`](@ref), [`lowrankdowndate!`](@ref).
