```
Array{T}(missing, dims)
Array{T,N}(missing, dims)
```

Construit un tableau `N`-dimensionnel [`Array`](@ref) contenant des éléments de type `T`, initialisé avec des entrées [`missing`](@ref). Le type d'élément `T` doit être capable de contenir ces valeurs, c'est-à-dire `Missing <: T`.

# Exemples

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing

julia> Array{Union{Missing, Int}}(missing, 2, 3)
2×3 Matrix{Union{Missing, Int64}}:
 missing  missing  missing
 missing  missing  missing
```
