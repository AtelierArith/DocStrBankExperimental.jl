```
<:(T1, T2)
```

Operador de subtipo: devuelve `true` si y solo si todos los valores del tipo `T1` también son del tipo `T2`.

# Ejemplos

```jldoctest
julia> Float64 <: AbstractFloat
true

julia> Vector{Int} <: AbstractArray
true

julia> Matrix{Float64} <: Matrix{AbstractFloat}
false
```
