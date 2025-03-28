```
Core.Type{T}
```

`Core.Type` est un type abstrait qui a tous les objets de type comme ses instances. La seule instance du type singleton `Core.Type{T}` est l'objet `T`.

# Exemples

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true
```
