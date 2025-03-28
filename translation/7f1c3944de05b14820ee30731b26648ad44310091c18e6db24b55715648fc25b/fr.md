```
filter(f, itr::SkipMissing{<:AbstractArray})
```

Renvoie un vecteur similaire au tableau enveloppé par l'itérateur `SkipMissing` donné, mais avec tous les éléments manquants et ceux pour lesquels `f` renvoie `false` supprimés.

!!! compat "Julia 1.2"
    Cette méthode nécessite Julia 1.2 ou une version ultérieure.


# Exemples

```jldoctest
julia> x = [1 2; missing 4]
2×2 Matrix{Union{Missing, Int64}}:
 1         2
  missing  4

julia> filter(isodd, skipmissing(x))
1-element Vector{Int64}:
 1
```
