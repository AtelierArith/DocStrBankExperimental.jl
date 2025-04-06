```
merge!(d::AbstractDict, others::AbstractDict...)
```

Actualiza la colección con pares de las otras colecciones. Ver también [`merge`](@ref).

# Ejemplos

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> merge!(d1, d2);

julia> d1
Dict{Int64, Int64} con 3 entradas:
  4 => 5
  3 => 4
  1 => 4
```
