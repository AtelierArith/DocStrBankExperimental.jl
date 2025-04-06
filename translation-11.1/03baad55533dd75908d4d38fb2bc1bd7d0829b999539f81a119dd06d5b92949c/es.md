```
eps(::Type{T}) donde T<:AbstractFloat
eps()
```

Devuelve el *epsilon de máquina* del tipo de punto flotante `T` (`T = Float64` por defecto). Esto se define como la brecha entre 1 y el siguiente valor más grande representable por `typeof(one(T))`, y es equivalente a `eps(one(T))`.  (Dado que `eps(T)` es un límite en el *error relativo* de `T`, es una cantidad "sin dimensiones" como [`one`](@ref).)

# Ejemplos

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
