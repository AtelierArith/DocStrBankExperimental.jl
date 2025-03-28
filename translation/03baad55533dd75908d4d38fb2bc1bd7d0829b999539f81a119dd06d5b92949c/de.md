```
eps(::Type{T}) where T<:AbstractFloat
eps()
```

Gibt die *Maschinen-Epsilon* des Fließkommatyps `T` zurück (`T = Float64` standardmäßig). Dies ist definiert als der Abstand zwischen 1 und dem nächstgrößeren Wert, der durch `typeof(one(T))` darstellbar ist, und entspricht `eps(one(T))`.  (Da `eps(T)` eine Schranke für den *relativen Fehler* von `T` ist, handelt es sich um eine "dimensionslose" Größe wie [`one`](@ref).)

# Beispiele

```jldoctest
julia> eps()
2.220446049250313e-16

julia> eps(Float32)
1.1920929f-7

julia> 1.0 + eps()
1.0000000000000002

julia> 1.0 + eps()/2
1.0
```
