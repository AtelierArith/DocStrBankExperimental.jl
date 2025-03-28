```
Array{T}(rien, dims)
Array{T,N}(rien, dims)
```

Construisez un tableau [`Array`](@ref) N-dimensionnel contenant des éléments de type `T`, initialisé avec des entrées [`nothing`](@ref). Le type d'élément `T` doit être capable de contenir ces valeurs, c'est-à-dire `Nothing <: T`.

# Exemples

```jldoctest
julia> Array{Union{Nothing, String}}(rien, 2)
2-element Vector{Union{Nothing, String}}:
 rien
 rien

julia> Array{Union{Nothing, Int}}(rien, 2, 3)
2×3 Matrix{Union{Nothing, Int64}}:
 rien  rien  rien
 rien  rien  rien
```
