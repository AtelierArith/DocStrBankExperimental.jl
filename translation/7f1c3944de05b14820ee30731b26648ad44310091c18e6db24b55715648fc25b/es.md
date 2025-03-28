```
filter(f, itr::SkipMissing{<:AbstractArray})
```

Devuelve un vector similar al array envuelto por el iterador `SkipMissing` dado, pero con todos los elementos faltantes y aquellos para los cuales `f` devuelve `false` eliminados.

!!! compat "Julia 1.2"
    Este método requiere Julia 1.2 o posterior.


# Ejemplos

```jldoctest
julia> x = [1 2; missing 4]
2×2 Matrix{Union{Missing, Int64}}:
 1         2
  missing  4

julia> filter(isodd, skipmissing(x))
1-element Vector{Int64}:
 1
```
