```
Vector{T}(rien, m)
```

Construit un [`Vector{T}`](@ref) de longueur `m`, initialisé avec des entrées [`rien`](@ref). Le type d'élément `T` doit être capable de contenir ces valeurs, c'est-à-dire `Nothing <: T`.

# Exemples

```jldoctest
julia> Vector{Union{Nothing, String}}(rien, 2)
2-element Vector{Union{Nothing, String}}:
 rien
 rien
```
