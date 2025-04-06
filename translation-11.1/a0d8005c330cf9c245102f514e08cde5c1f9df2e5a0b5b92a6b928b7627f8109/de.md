```
<:(T1, T2)
```

Subtypoperator: gibt `true` zurück, wenn und nur wenn alle Werte des Typs `T1` auch vom Typ `T2` sind.

# Beispiele

```jldoctest
julia> Float64 <: AbstractFloat
true

julia> Vector{Int} <: AbstractArray
true

julia> Matrix{Float64} <: Matrix{AbstractFloat}
false
```
