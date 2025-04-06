```
merge!(d::AbstractDict, others::AbstractDict...)
```

Met à jour la collection avec des paires des autres collections. Voir aussi [`merge`](@ref).

# Exemples

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> merge!(d1, d2);

julia> d1
Dict{Int64, Int64} avec 3 entrées :
  4 => 5
  3 => 4
  1 => 4
```
