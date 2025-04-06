```
findfirst(A)
```

Devuelve el índice o clave del primer valor `true` en `A`. Devuelve `nothing` si no se encuentra tal valor. Para buscar otros tipos de valores, pasa un predicado como el primer argumento.

Los índices o claves son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

Véase también: [`findall`](@ref), [`findnext`](@ref), [`findlast`](@ref), [`searchsortedfirst`](@ref).

# Ejemplos

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findfirst(A)
3

julia> findfirst(falses(3)) # devuelve nothing, pero no se imprime en el REPL

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findfirst(A)
CartesianIndex(2, 1)
```
