```
merge!(d::AbstractDict, others::AbstractDict...)
```

Aktualisiere die Sammlung mit Paaren aus den anderen Sammlungen. Siehe auch [`merge`](@ref).

# Beispiele

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> merge!(d1, d2);

julia> d1
Dict{Int64, Int64} mit 3 Einträgen:
  4 => 5
  3 => 4
  1 => 4
```
