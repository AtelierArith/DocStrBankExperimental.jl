```
indexin(a, b)
```

Devuelve un array que contiene el primer índice en `b` para cada valor en `a` que es un miembro de `b`. El array de salida contiene `nothing` donde quiera que `a` no sea un miembro de `b`.

Véase también: [`sortperm`](@ref), [`findfirst`](@ref).

# Ejemplos

```jldoctest
julia> a = ['a', 'b', 'c', 'b', 'd', 'a'];

julia> b = ['a', 'b', 'c'];

julia> indexin(a, b)
6-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
 2
  nothing
 1

julia> indexin(b, a)
3-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
```
