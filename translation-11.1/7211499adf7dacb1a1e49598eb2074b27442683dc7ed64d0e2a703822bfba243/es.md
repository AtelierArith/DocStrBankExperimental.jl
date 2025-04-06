```
clamp(x, T)::T
```

Limita `x` entre `typemin(T)` y `typemax(T)` y convierte el resultado al tipo `T`.

Véase también [`trunc`](@ref).

# Ejemplos

```jldoctest
julia> clamp(200, Int8)
127

julia> clamp(-200, Int8)
-128

julia> trunc(Int, 4pi^2)
39
```
