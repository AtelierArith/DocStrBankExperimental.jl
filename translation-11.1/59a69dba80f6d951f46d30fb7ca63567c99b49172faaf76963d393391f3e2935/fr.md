```
empty(v::AbstractVector, [eltype])
```

Crée un vecteur vide similaire à `v`, en changeant éventuellement le `eltype`.

Voir aussi : [`empty!`](@ref), [`isempty`](@ref), [`isassigned`](@ref).

# Exemples

```jldoctest
julia> empty([1.0, 2.0, 3.0])
Float64[]

julia> empty([1.0, 2.0, 3.0], String)
String[]
```
