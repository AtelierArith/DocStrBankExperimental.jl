```
insert!(a::Vector, index::Integer, item)
```

Inserta un `item` en `a` en el índice dado `index`. `index` es el índice de `item` en el resultado de `a`.

Véase también: [`push!`](@ref), [`replace`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Ejemplos

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
