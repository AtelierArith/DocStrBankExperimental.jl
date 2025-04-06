```
insert!(a::Vector, index::Integer, item)
```

Insérer un `item` dans `a` à l'index donné. `index` est l'index de `item` dans le `a` résultant.

Voir aussi : [`push!`](@ref), [`replace`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Exemples

```jldoctest
julia> insert!(Any[1:6;], 3, "here")
7-element Vector{Any}:
 1
 2
  "here"
 3
 4
 5
 6
```
