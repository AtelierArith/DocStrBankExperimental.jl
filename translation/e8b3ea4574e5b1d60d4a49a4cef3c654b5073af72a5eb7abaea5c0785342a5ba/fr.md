```
values(iterator)
```

Pour un itérateur ou une collection qui a des clés et des valeurs, renvoie un itérateur sur les valeurs. Cette fonction renvoie simplement son argument par défaut, puisque les éléments d'un itérateur général sont normalement considérés comme ses "valeurs".

# Exemples

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> values(d)
ValueIterator for a Dict{String, Int64} with 2 entries. Values:
  2
  1

julia> values([2])
1-element Vector{Int64}:
 2
```
