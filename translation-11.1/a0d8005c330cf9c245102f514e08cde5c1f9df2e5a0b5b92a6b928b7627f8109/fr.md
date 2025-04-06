```
<:(T1, T2)
```

Opérateur de sous-type : renvoie `true` si et seulement si toutes les valeurs de type `T1` sont également de type `T2`.

# Exemples

```jldoctest
julia> Float64 <: AbstractFloat
true

julia> Vector{Int} <: AbstractArray
true

julia> Matrix{Float64} <: Matrix{AbstractFloat}
false
```
